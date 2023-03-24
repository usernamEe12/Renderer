cmake_minimum_required(VERSION 3.4.1)
project(Renderer)

set(CMAKE_CXX_STANDARD 11)

set(GLAD_H ${PROJECT_SOURCE_DIR}/include)
set(GLFW_H ${PROJECT_SOURCE_DIR}/include)
include_directories(${GLAD_H} ${GLFW_H})

set(GLFW_LINK ${PROJECT_SOURCE_DIR}/pkg/lib/libglfw.3.dylib)
link_libraries(${GLFW_LINK})

set(SOURCES src/glad.c main.cpp)
add_executable(Renderer ${SOURCES})

if(APPLE)
   target_link_libraries(Renderer "-framework OpenGL")
endif()

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(Cpack)



