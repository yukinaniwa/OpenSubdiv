#
#   Copyright 2013 Pixar
#
#   Licensed under the Apache License, Version 2.0 (the "Apache License")
#   with the following modification; you may not use this file except in
#   compliance with the Apache License and the following modification to it:
#   Section 6. Trademarks. is deleted and replaced with:
#
#   6. Trademarks. This License does not grant permission to use the trade
#      names, trademarks, service marks, or product names of the Licensor
#      and its affiliates, except as required to comply with Section 4(c) of
#      the License and to reproduce the content of the NOTICE file.
#
#   You may obtain a copy of the Apache License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the Apache License with the above modification is
#   distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
#   KIND, either express or implied. See the Apache License for the specific
#   language governing permissions and limitations under the Apache License.
#

# *** paintTest ***

set(SHADER_FILES
     shader.glsl
     paintShader.glsl
)

set(PLATFORM_LIBRARIES
    ${OSD_LINK_TARGET}
    ${OPENGL_LIBRARY}
    ${GLEW_LIBRARY}
    ${GLFW_LIBRARIES}
)

include_directories(
    ${PROJECT_SOURCE_DIR}/opensubdiv
    ${PROJECT_SOURCE_DIR}/regression
    ${GLEW_INCLUDE_DIR}
    ${GLFW_INCLUDE_DIR}
)

_stringify("${SHADER_FILES}" INC_FILES)

include_directories(${CMAKE_CURRENT_BINARY_DIR})

_add_glfw_executable(paintTest
    main.cpp
    ${SHADER_FILES}
    ${INC_FILES}
    $<TARGET_OBJECTS:examples_common_obj>
)

target_link_libraries(paintTest
    ${PLATFORM_LIBRARIES}
)

install(TARGETS paintTest DESTINATION ${CMAKE_BINDIR_BASE})
