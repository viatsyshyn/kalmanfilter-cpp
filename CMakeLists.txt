cmake_minimum_required(VERSION 3.28)

include("cmake/HunterGate.cmake")

HunterGate(
        URL "https://github.com/cpp-pm/hunter/archive/v0.25.5.tar.gz"
        SHA1 "a20151e4c0740ee7d0f9994476856d813cdead29"
)

project(kalmanfilter)

set(HUNTER_STATUS_DEBUG ON)

hunter_add_package(Eigen)

set(CMAKE_CXX_STANDARD 26)

# ----------------------------------------
# Eigen
# ----------------------------------------
find_package(Eigen3 REQUIRED CONFIG)

set(SOURCE_FILES src/kalman-filter.cpp kalman-test.cpp)

add_executable(kalman-test ${SOURCE_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC Eigen3::Eigen)
