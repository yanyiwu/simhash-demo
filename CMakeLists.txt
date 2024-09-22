CMAKE_MINIMUM_REQUIRED (VERSION 3.14)
PROJECT(CPPJIEBA-DEMO)

include(FetchContent)

FetchContent_Declare(simhash
    GIT_REPOSITORY https://github.com/yanyiwu/simhash.git
    GIT_TAG master
)
FetchContent_MakeAvailable(simhash)

# Add these lines to set up include directories
include_directories(${simhash_SOURCE_DIR}/include 
	${simhash_SOURCE_DIR}/submodules/cppjieba/include
	${simhash_SOURCE_DIR}/submodules/cppjieba/deps/limonp/include)

if(NOT DEFINED CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 11)
endif()
ADD_DEFINITIONS(-O3 -g)
ADD_EXECUTABLE(demo demo.cpp)
enable_testing()
ADD_TEST(NAME demo COMMAND ./demo)
