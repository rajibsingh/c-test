cmake_minimum_required(VERSION 3.12)
project(c_test)
FILE(GLOB SOURCE_FILES src/*.c)

add_executable(
        demo
        ${SOURCE_FILES}
        deps/glew/src/glew.c
        deps/lodepng/lodepng.c
        deps/noise/noise.c
        deps/sqlite/sqlite3.c
        deps/tinycthread/tinycthread.c)
#)

#find_package(OpenGL REQUIRED)
#include_directories(${OPENGL_INCLUDE_DIR})
#target_link_libraries(demo ${OPENGL_LIBRARIES})
#find_library(carbon_lib Carbon) # we look for the Carbon framework and use carbon_lib as an alias for it
#find_library(cocoa_lib Cocoa)
find_library(opengl_lib OpenGL)
#find_library(corefoundation_lib CoreFoundation)

set(frameworks
#        ${carbon_lib}
#        ${cocoa_lib}
        ${opengl_lib}
#        ${corefoundation_lib})
)

target_link_libraries(demo -lglfw ${frameworks})
#add_library(demo STATIC ${sources})

#target_link_libraries(demo stdc++ "-framework Foundation" "-framework Cocoa" objc)

add_definitions(-std=c99 -O3)

add_subdirectory(deps/glfw)
include_directories(deps/glew/include)
include_directories(deps/glfw/include)
include_directories(deps/lodepng)
include_directories(deps/noise)
include_directories(deps/sqlite)
include_directories(deps/tinycthread)


#set(CMAKE_C_STANDARD 99)

add_executable(c_test main.c)