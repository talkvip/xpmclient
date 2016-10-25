Primecoin XPM GPU Miner for xpmpool (aka. madPrimeMiner)
==============

XPM Miner topic: https://bitcointalk.org/index.php?topic=831708.0
ZCash Miner topic: https://bitcointalk.org/index.php?topic=1660023.0
--------------

The miner works with:
- OpenCL (AMD or NVidia)
- ZEROMQ message system & CZMQ library (+ libsodium on Linux)
- Google protobuf protocol
- GMP
- CMake build system

How to compile:
- Build dependencies
- Create directory for build client
- Run cmake and make:

Ubuntu building commands:

sudo apt-get install libprotobuf-dev protobuf-compiler libzmq5-dev libczmq-dev libgmp-dev libssl-dev libsodium-dev
cmake ../xpmclient -DOPENCL_LIBRARY=/usr/lib/x86_64-linux-gnu/libOpenCL.so -DOPENCL_INCLUDE_DIRECTORY=/opt/AMDAPPSDK-3.0/include
make -j5

"../xpmclient" - directory with client source;

/usr/lib/x86_64-linux-gnu/libOpenCL.so - path to OpenCL library in AMD APP SDK directory

For static build on linux (without additional dependencies) run:

cmake ../xpmclient -DInstallPrefix=/opt/x86_64-Linux-static -DSTATIC_BUILD=1 -DOPENCL_LIBRARY=/usr/lib/x86_64-linux-gnu/libOpenCL.so -DOPENCL_INCLUDE_DIRECTORY=/opt/AMDAPPSDK-3.0/include

/opt/x86_64-Linux-static - directory with static builds of ZMQ, CZMQ, GMP, protobuf

For cross-compiling for Windows using mingw:

cmake ../xpmclient -DCMAKE_TOOLCHAIN_FILE=../xpmclient/cmake/Toolchain-cross-mingw32-linux.cmake -DInstallPrefix=/opt/mingw32 -DOPENCL_LIBRARY=/opt/mingw32/lib/x86/OpenCL.lib

/opt/mingw32 - install directory for mingw builds of libraries ZMQ, CZMQ, GMP, protobuf

/opt/mingw32/lib/x86/OpenCL.lib - path to OpenCL library for Win32

