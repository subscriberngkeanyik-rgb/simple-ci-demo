cmake_minimum_required(VERSION 3.24) # 建议最低版本设为 3.24 以更好支持 CMP0135
cmake_policy(SET CMP0135 NEW)
project(SimpleCIDemo)

set(CMAKE_CXX_STANDARD 11)

include(FetchContent)
FetchContent_Declare(
googletest
URL https://github.com/google/googletest/archive/refs/heads/main.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(runTests
calculator.cpp
test_calculator.cpp
)

target_link_libraries(runTests gtest_main)
include(GoogleTest)
gtest_discover_tests(runTests)
