#
# project: fips-optick
#
if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    project(fips-optick)
    fips_setup()
endif()

fips_begin_module(optick)
    # TODO: Make vulkan support configurable
    fips_files_ex(optick/src/ *.cpp EXCEPT *.vulkan.cpp)
fips_end_module()
target_include_directories(optick PUBLIC optick/src/)

if (NOT FIPS_IMPORT)
    fips_finish()
endif()