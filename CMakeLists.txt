cmake_minimum_required(VERSION 3.10)

project(sxmdb CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_DISABLE_IN_SOURCE_BUILD ON)
set(CMAKE_DISABLE_SOURCE_CHANGES ON)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fpermissive -Wall" )

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} \
# -O3 -mfpmath=sse -msse2 -msse3 -msse4.2 -ffast-math -funsafe-math-optimizations \
# -mfma -mfma4 -mavx -funsafe-loop-optimizations -funswitch-loops \
# -fvariable-expansion-in-unroller -Wall"
#)

set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS}" )
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS}" )

SET( HEADERS ${PROJECT_SOURCE_DIR}
    src/midl.h
    include/lmdb.h
)

source_group("HEADERS" FILES ${HEADERS})

SET( SOURCES ${PROJECT_SOURCE_DIR}
    src/mdb.cpp
    src/midl.cpp
    test/mtest.cpp
)

source_group("SOURCES" FILES ${SOURCES})

include_directories(
    include
)

set(CMAKE_BUILD_TYPE DE CACHE STRING "" FORCE)

add_executable( ${PROJECT_NAME}
    ${SOURCES}
    ${HEADERS}
)

target_link_libraries( ${PROJECT_NAME}
    pthread
)
