project(GPU-path-tracing-tutorial-4 LANGUAGES CXX CUDA)

cmake_minimum_required(VERSION 2.8)

set(_VCPKG_INCLUDE_DIR "${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/")

find_package(glew REQUIRED)
find_package(glut REQUIRED)
find_package(opengl REQUIRED)

set(HEADERS
    Array.h
    BVH.h
    BVHNode.h
    Camera.h
    CudaBVH.h
    CudaRenderKernel.h
    Geometry.h
    HDRloader.h
    MouseKeyboardInput.h
    Scene.h
    SceneLoader.h
    Sort.h
    SplitBVHBuilder.h
    Util.h
    cutil_math.h
    linear_math.h
)

set(SOURCES
    BVH.cpp
    BVHNode.cpp
    Camera.cpp
    CudaBVH.cpp
    HDRloader.cpp
    main.cpp
    renderkernel.cu
    SceneLoader.cpp
    Sort.cpp
    SplitBVHBuilder.cpp
    Util.cpp
)

add_executable(tutorial4 ${HEADERS} ${SOURCES})

target_link_libraries(tutorial4 cuda cudart)

include_directories(${_VCPKG_INCLUDE_DIR})