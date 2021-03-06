#
# Copyright 2010-2011,2013-2015 Ettus Research LLC
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

ADD_SUBDIRECTORY(transport)
ADD_SUBDIRECTORY(types)
ADD_SUBDIRECTORY(usrp)
ADD_SUBDIRECTORY(usrp_clock)
ADD_SUBDIRECTORY(utils)

CONFIGURE_FILE(
    ${CMAKE_CURRENT_SOURCE_DIR}/version.hpp.in
    ${CMAKE_CURRENT_BINARY_DIR}/version.hpp
)

UHD_INSTALL(FILES
    build_info.hpp
    config.hpp
    convert.hpp
    deprecated.hpp
    device.hpp
    device_deprecated.ipp
    exception.hpp
    property_tree.ipp
    property_tree.hpp
    stream.hpp
    ${CMAKE_CURRENT_BINARY_DIR}/version.hpp
    DESTINATION ${INCLUDE_DIR}/uhd
    COMPONENT headers
)

IF(ENABLE_C_API)
    UHD_INSTALL(FILES
        config.h
        error.h
        DESTINATION ${INCLUDE_DIR}/uhd
        COMPONENT headers
    )
ENDIF(ENABLE_C_API)
