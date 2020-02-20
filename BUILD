config_setting(
    name = "k8-gcc4.8",
    values = {"cpu": "k8"},
)

config_setting(
    name = "k8-gcc5.4",
    define_values = {
     "gcc": "5.4",   
    },
    values = {"cpu": "k8"},
)

config_setting(
    name = "aarch64",
    values = {"cpu": "aarch64"},
)

filegroup(
    name = "empty",
    srcs = [],
)


cc_library(
    name = "protobuf",
    srcs = select({
        ":k8-gcc4.8": glob(["lib/*.so*"]),
        ":k8-gcc5.4": glob(["lib-gcc5.4/*.so*"]),
        ":aarch64": glob(["lib-aarch64/*.a*"]),
        "//conditions:default": [":empty"]
    }),
    hdrs = glob(["src/**/*.h"]),
    copts = COPTS,
    includes = ["src/"],
    linkopts = LINK_OPTS,
    visibility = ["//visibility:public"],
    deps = [":protobuf_lite"],
)

cc_library(
    name = "protobuf_lite",
    srcs = select({
        ":k8-gcc4.8": glob(["lib/*.so*"]),
        ":k8-gcc5.4": glob(["lib-gcc5.4/*.so*"]),
        ":aarch64": glob(["lib-aarch64/*.a*"]),
        "//conditions:default": [":empty"]
    }),
    hdrs = glob(["src/google/protobuf/**/*.h"]),
    copts = COPTS,
    includes = ["src/"],
    linkopts = LINK_OPTS,
    visibility = ["//visibility:public"],
)
