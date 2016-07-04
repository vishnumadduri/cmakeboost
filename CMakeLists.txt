cmake_minimum_required (VERSION 2.8)
project (CMakeHelloWorld)

#version number
set (CMakeHelloWorld_VERSION_MAJOR 1)
set (CMakeHelloWorld_VERSION_MINOR 0)
set (Boost_USE_MULTITHREADED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x -Wall ")
FIND_PACKAGE(PkgConfig)
FIND_PACKAGE(Boost  REQUIRED COMPONENTS thread system)

#include the subdirectory containing our libs
include_directories(${Boost_INCLUDE_DIR})
message(STATUS "BOOST INC  set to ${Boost_INCLUDE_DIR} lib ${Boost_LIBRARIES}" )
#indicate the entry point for the executable
add_executable (CMakeHelloWorld  HelloWorld.cpp)

# Indicate which libraries to include during the link process.
target_link_libraries (CMakeHelloWorld  ${Boost_LIBRARIES})

install (TARGETS CMakeHelloWorld DESTINATION bin)
