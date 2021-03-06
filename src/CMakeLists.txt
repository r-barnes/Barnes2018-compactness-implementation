cmake_minimum_required (VERSION 3.9)

add_executable(augmenter.exe augmenter.cpp)

target_link_libraries(augmenter.exe
PRIVATE
  compactnesslib
)

target_compile_features(augmenter.exe PUBLIC cxx_std_11)

add_executable(koch.exe koch.cpp)

target_compile_features(koch.exe PUBLIC cxx_std_11)

install(
  TARGETS koch.exe augmenter.exe
  RUNTIME DESTINATION ${CMAKE_SOURCE_DIR}/bin
)

install(
  FILES common.py 
  DESTINATION ${CMAKE_SOURCE_DIR}/bin
  PERMISSIONS OWNER_READ
)

install(
  FILES res_bounded.py res_fig_gerrymandering.py res_projections.py res_simp_indiv.py res_simp_together.py make_figs.R koch_scores.py districtplot.py
  DESTINATION ${CMAKE_SOURCE_DIR}/bin
  PERMISSIONS OWNER_READ OWNER_EXECUTE
)
