cmake_minimum_required(VERSION 3.28)
project (uSockets)

file(GLOB C_SOURCES src/*.c src/eventing/*.c src/crypto/*.c src/io_uring/*.c)

add_library(uSockets STATIC ${C_SOURCES})
set_property(TARGET uSockets PROPERTY C_STANDARD 11)
target_include_directories(uSockets PUBLIC src)
target_compile_definitions(uSockets PUBLIC WITH_QUIC WITH_WOLFSSL)


#clang -I/opt/homebrew/opt/llvm/include -flto -DLIBUS_NO_SSL -std=c11 -Isrc -O3 -c src/*.c src/eventing/*.c src/crypto/*.c src/io_uring/*.c
#llvm-lib /out:uSockets.a *.o
#llvm-ar rvs uSockets.a *.o
