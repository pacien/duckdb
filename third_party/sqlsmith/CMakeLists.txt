include_directories(include)

include_directories(../../extension/tpch/include)

add_executable(
  sqlsmith
  duckdb.cc
  dump.cc
  expr.cc
  grammar.cc
  impedance.cc
  log.cc
  prod.cc
  random.cc
  relmodel.cc
  schema.cc
  sqlsmith.cc)
target_link_libraries(sqlsmith duckdb tpch_extension)
target_link_libraries(sqlsmith Threads::Threads)

set_target_properties(
  sqlsmith
  PROPERTIES
    COMPILE_FLAGS
    "-Wno-potentially-evaluated-expression -Wno-delete-non-virtual-dtor")
