cmake_minimum_required(VERSION 3.5)
project(lcms2)

set(SOURCES src/cmsalpha.c
            src/cmscam02.c
            src/cmscgats.c
            src/cmscnvrt.c
            src/cmserr.c
            src/cmsgamma.c
            src/cmsgmt.c
            src/cmshalf.c
            src/cmsintrp.c
            src/cmsio0.c
            src/cmsio1.c
            src/cmslut.c
            src/cmsmd5.c
            src/cmsmtrx.c
            src/cmsnamed.c
            src/cmsopt.c
            src/cmspack.c
            src/cmspcs.c
            src/cmsplugin.c
            src/cmsps2.c
            src/cmssamp.c
            src/cmssm.c
            src/cmstypes.c
            src/cmsvirt.c
            src/cmswtpnt.c
            src/cmsxform.c
            src/lcms2_internal.h)

set(HEADERS include/lcms2.h
            include/lcms2_plugin.h)

add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS})
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)

install(TARGETS ${PROJECT_NAME} EXPORT ${PROJECT_NAME}
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

if(MSVC AND BUILD_SHARED_LIBS)
  install(FILES $<TARGET_PDB_FILE:${PROJECT_NAME}> DESTINATION lib)
endif()

install(FILES ${HEADERS} DESTINATION include)
