cmake_minimum_required(VERSION 3.5)
#
# Checking for most recent ESP-IDF
#
message("ESP_IDF path: " $ENV{IDF_PATH})
message("Project path: " ${CMAKE_CURRENT_SOURCE_DIR})

execute_process(COMMAND "git" "pull" WORKING_DIRECTORY $ENV{IDF_PATH})
execute_process(COMMAND "git" "submodule" "update" "--init" "--recursive" WORKING_DIRECTORY $ENV{IDF_PATH} RESULT_VARIABLE git_result OUTPUT_VARIABLE git_out)

#
# Setting linker settings for components
#
include($ENV{IDF_PATH}/tools/cmake/project.cmake)
project(app)
