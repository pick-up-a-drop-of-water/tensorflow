load("//tensorflow:tensorflow.bzl", "tf_py_wrap_cc")

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],  # Apache 2.0
)

cc_library(
    name = "numpy",
    srcs = ["numpy.cc"],
    hdrs = ["numpy.h"],
    deps = [
        "//third_party/py/numpy:headers",
        "//third_party/python_runtime:headers",
    ],
)

cc_library(
    name = "interpreter_wrapper_lib",
    srcs = ["interpreter_wrapper.cc"],
    hdrs = ["interpreter_wrapper.h"],
    deps = [
        ":numpy",
        ":python_error_reporter",
        ":python_utils",
        "//tensorflow/lite:framework",
        "//tensorflow/lite:string_util",
        "//tensorflow/lite/c:c_api_internal",
        "//tensorflow/lite/kernels:builtin_ops",
        "//third_party/py/numpy:headers",
        "//third_party/python_runtime:headers",
        "@com_google_absl//absl/memory",
    ],
)

cc_library(
    name = "python_error_reporter",
    srcs = ["python_error_reporter.cc"],
    hdrs = ["python_error_reporter.h"],
    deps = [
        "//tensorflow/lite/core/api",
        "//third_party/python_runtime:headers",
    ],
)

cc_library(
    name = "python_utils",
    srcs = ["python_utils.cc"],
    hdrs = ["python_utils.h"],
    deps = [
        ":numpy",
        "//tensorflow/lite:framework",
        "//tensorflow/lite:string_util",
        "//third_party/py/numpy:headers",
        "//third_party/python_runtime:headers",
    ],
)

tf_py_wrap_cc(
    name = "tensorflow_wrap_interpreter_wrapper",
    srcs = [
        "interpreter_wrapper.i",
    ],
    deps = [
        ":interpreter_wrapper_lib",
        "//third_party/python_runtime:headers",
    ],
)
