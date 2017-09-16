cmake_minimum_required(VERSION 3.0)

project(BreezeExtraIcons VERSION 0.1)

# ECM setup
include(FeatureSummary)
find_package(ECM 5.38.0  NO_MODULE)
set_package_properties(ECM PROPERTIES TYPE REQUIRED DESCRIPTION "Extra CMake Modules." URL "https://projects.kde.org/projects/kdesupport/extra-cmake-modules")
feature_summary(WHAT REQUIRED_PACKAGES_NOT_FOUND FATAL_ON_MISSING_REQUIRED_PACKAGES)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
#include(GtkUpdateIconCache)

option(SKIP_INSTALL_ICONS "Skip installing the icons files" OFF)


########### install files ###############

set( breeze_icon_dirs  places )

set(BREEZE_INSTALL_DIR ${KDE_INSTALL_FULL_ICONDIR}/breeze)

if (NOT SKIP_INSTALL_ICONS)
    install( DIRECTORY ${breeze_icon_dirs} DESTINATION ${BREEZE_INSTALL_DIR} )
endif()

#gtk_update_icon_cache(${BREEZE_INSTALL_DIR})

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES INCLUDE_QUIET_PACKAGES)
