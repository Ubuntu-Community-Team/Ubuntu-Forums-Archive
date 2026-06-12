---
title: "boost 1.51.0 installation '30 targets failed'"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by an0nym1ty on 2012-09-19
I've been just #including my boost libraries up until now to get around this issue, but now i need to use cmake so i need the libraries and a proper install of boost... this is what's happening when i use sudo ./b2 install threading=multi link=shared (as prescribed by [http://www.linuxfromscratch.org/blfs/view/cvs/general/boost.html]("these instructions")


```
gcc.compile.c++ bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/zlib.o
libs/iostreams/src/zlib.cpp:20:76: fatal error: zlib.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_IOSTREAMS_DYN_LINK=1 -DBOOST_IOSTREAMS_USE_DEPRECATED -DNDEBUG  -I"." -c -o "bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/zlib.o" "libs/iostreams/src/zlib.cpp"

...failed gcc.compile.c++ bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/zlib.o...
gcc.compile.c++ bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/bzip2.o
libs/iostreams/src/bzip2.cpp:20:56: fatal error: bzlib.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_IOSTREAMS_DYN_LINK=1 -DBOOST_IOSTREAMS_USE_DEPRECATED -DNDEBUG  -I"." -c -o "bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/bzip2.o" "libs/iostreams/src/bzip2.cpp"

...failed gcc.compile.c++ bin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi/bzip2.o...
...skipped <pbin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi>libboost_iostreams.so.1.51.0 for lack of <pbin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi>zlib.o...
...skipped <p/usr/lib>libboost_iostreams.so.1.51.0 for lack of <pbin.v2/libs/iostreams/build/gcc-4.6/release/threading-multi>libboost_iostreams.so.1.51.0...
...skipped <p/usr/lib>libboost_iostreams.so for lack of <p/usr/lib>libboost_iostreams.so.1.51.0...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/numeric.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/numeric.hpp:8,
                 from libs/python/src/numeric.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/numeric.o" "libs/python/src/numeric.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/numeric.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/list.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/list.hpp:8,
                 from libs/python/src/list.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/list.o" "libs/python/src/list.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/list.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/long.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/long.hpp:8,
                 from libs/python/src/long.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/long.o" "libs/python/src/long.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/long.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/dict.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/dict.hpp:8,
                 from libs/python/src/dict.cpp:4:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/dict.o" "libs/python/src/dict.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/dict.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/tuple.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/tuple.hpp:8,
                 from libs/python/src/tuple.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/tuple.o" "libs/python/src/tuple.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/tuple.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/str.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/str.hpp:8,
                 from libs/python/src/str.cpp:4:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/str.o" "libs/python/src/str.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/str.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/slice.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/slice.hpp:9,
                 from libs/python/src/slice.cpp:1:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/slice.o" "libs/python/src/slice.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/slice.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/from_python.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/converter/from_python.hpp:8,
                 from libs/python/src/converter/from_python.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/from_python.o" "libs/python/src/converter/from_python.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/from_python.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/registry.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/converter/registry.hpp:7,
                 from libs/python/src/converter/registry.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/registry.o" "libs/python/src/converter/registry.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/registry.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/type_id.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/type_id.hpp:8,
                 from libs/python/src/converter/type_id.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/type_id.o" "libs/python/src/converter/type_id.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/type_id.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/enum.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object_core.hpp:10,
                 from ./boost/python/object/enum_base.hpp:8,
                 from libs/python/src/object/enum.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/enum.o" "libs/python/src/object/enum.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/enum.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/class.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from libs/python/src/object/class.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/class.o" "libs/python/src/object/class.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/class.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object/function.hpp:8,
                 from ./boost/python/docstring_options.hpp:8,
                 from libs/python/src/object/function.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function.o" "libs/python/src/object/function.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/inheritance.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/type_id.hpp:8,
                 from ./boost/python/object/inheritance.hpp:8,
                 from libs/python/src/object/inheritance.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/inheritance.o" "libs/python/src/object/inheritance.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/inheritance.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/life_support.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object/life_support.hpp:7,
                 from libs/python/src/object/life_support.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/life_support.o" "libs/python/src/object/life_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/life_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/pickle_support.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/make_function.hpp:8,
                 from libs/python/src/object/pickle_support.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/pickle_support.o" "libs/python/src/object/pickle_support.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/pickle_support.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/errors.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/errors.hpp:12,
                 from libs/python/src/errors.cpp:10:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/errors.o" "libs/python/src/errors.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/errors.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/module.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/scope.hpp:8,
                 from libs/python/src/module.cpp:9:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/module.o" "libs/python/src/module.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/module.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/builtin_converters.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/handle.hpp:8,
                 from libs/python/src/converter/builtin_converters.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/builtin_converters.o" "libs/python/src/converter/builtin_converters.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/builtin_converters.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/arg_to_python_base.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/handle.hpp:8,
                 from ./boost/python/converter/arg_to_python_base.hpp:7,
                 from libs/python/src/converter/arg_to_python_base.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/arg_to_python_base.o" "libs/python/src/converter/arg_to_python_base.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/converter/arg_to_python_base.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/iterator.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object_fwd.hpp:8,
                 from ./boost/python/object/iterator_core.hpp:8,
                 from libs/python/src/object/iterator.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/iterator.o" "libs/python/src/object/iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/stl_iterator.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from libs/python/src/object/stl_iterator.cpp:10:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/stl_iterator.o" "libs/python/src/object/stl_iterator.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/stl_iterator.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_protocol.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object_protocol.hpp:8,
                 from libs/python/src/object_protocol.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_protocol.o" "libs/python/src/object_protocol.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_protocol.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_operators.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/object_operators.hpp:8,
                 from libs/python/src/object_operators.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_operators.o" "libs/python/src/object_operators.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object_operators.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/wrapper.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/detail/wrapper_base.hpp:7,
                 from ./boost/python/wrapper.hpp:7,
                 from libs/python/src/wrapper.cpp:5:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/wrapper.o" "libs/python/src/wrapper.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/wrapper.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/import.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/import.hpp:8,
                 from libs/python/src/import.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/import.o" "libs/python/src/import.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/import.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/exec.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/ssize_t.hpp:9,
                 from ./boost/python/object.hpp:8,
                 from ./boost/python/exec.hpp:8,
                 from libs/python/src/exec.cpp:6:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/exec.o" "libs/python/src/exec.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/exec.o...
gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function_doc_signature.o
In file included from ./boost/python/detail/prefix.hpp:13:0,
                 from ./boost/python/converter/registrations.hpp:8,
                 from libs/python/src/object/function_doc_signature.cpp:9:
./boost/python/detail/wrap_python.hpp:75:24: fatal error: patchlevel.h: No such file or directory
compilation terminated.

    "g++"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_PYTHON_SOURCE -DNDEBUG  -I"." -I"/usr/include/python2.7" -c -o "bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function_doc_signature.o" "libs/python/src/object/function_doc_signature.cpp"

...failed gcc.compile.c++ bin.v2/libs/python/build/gcc-4.6/release/threading-multi/object/function_doc_signature.o...
...skipped <pbin.v2/libs/python/build/gcc-4.6/release/threading-multi>libboost_python.so.1.51.0 for lack of <pbin.v2/libs/python/build/gcc-4.6/release/threading-multi>numeric.o...
...skipped <p/usr/lib>libboost_python.so.1.51.0 for lack of <pbin.v2/libs/python/build/gcc-4.6/release/threading-multi>libboost_python.so.1.51.0...
...skipped <p/usr/lib>libboost_python.so for lack of <p/usr/lib>libboost_python.so.1.51.0...
...failed updating 30 targets...
...skipped 6 targets...

```

Halp? = /  they all have to do with python... i'm not sure why.

thanks

---

