cmake_minimum_required(VERSION 3.7)
project(research_ocr)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        src/Alphabet.cpp
        src/Alphabet.h
        src/Letter.cpp
        src/Letter.h
        src/main.cpp
        src/matrix.cpp
        src/matrix.h)

add_executable(research_ocr ${SOURCE_FILES})

# Credit for the following to: https://github.com/SFML/SFML/wiki/Tutorial%3A-Build-your-SFML-project-with-CMake
# Detect and add SFML
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})
#Find any version 2.X of SFML
#See the FindSFML.cmake file for additional details and instructions
# network audio
find_package(SFML 2 REQUIRED network audio graphics window system)
if(SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(research_ocr ${EXECUTABLE_NAME} ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
endif()
