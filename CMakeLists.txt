project(WS_server LANGUAGES CXX)

cmake_minimum_required(VERSION 3.19)

set(CMAKE_CXX_STANDARD 20)
set(BOOST_ROOT  "/home/alex/boost_1_76_0")
set (Boost_USE_STATIC_LIBS ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

find_package (Boost 1.76.0 COMPONENTS system iostreams filesystem)
include_directories (${Boost_INCLUDE_DIRS})
include_directories (${OpenSSL_INCLUDE_DIRS})
#add_library(${PROJECT_NAME} SHARED main.cpp)
add_executable(${PROJECT_NAME} main.cpp session.h session.cpp listener.h listener.cpp)# fail.cpp)

link_directories(${PROJECT_NAME}  ${Boost_LIBRARY_DIRS})
target_link_libraries (${PROJECT_NAME}  ${Boost_LIBRARIES})
