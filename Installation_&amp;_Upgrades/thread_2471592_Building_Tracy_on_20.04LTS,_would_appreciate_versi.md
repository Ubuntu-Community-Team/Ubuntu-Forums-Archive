---
title: "Building Tracy on 20.04LTS, would appreciate version advice."
date: 2022-02-03
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2022-02-03
I have to build the Tracy profile for Ubuntu 20.04 LTS.  Build errors include:

Tracy build instructions from early 2021:
To build the application contained in the profiler directory, you will need to install external libraries, which
are not bundled with Tracy.
Capstone library At the time of writing, the capstone library is in a bit of disarray. The officially released
version 4.0.2 can’t disassemble some AVX instructions, which are successfully parsed by the next branch.
However, the next branch somehow lost information about input/output registers for some functions. You
may want to explore the various available versions to find one that suits your needs the best.

-------------------
make[1]: Entering directory '/home/john/local/tracy/profiler/build/unix'
Package capstone was not found in the pkg-config search path.
Package glfw3 was not found in the pkg-config search path.
Package gtk+-3.0 was not found in the pkg-config search path.

../../../imgui/misc/freetype/imgui_freetype.cpp:38:10: fatal error: ft2build.h: No such file or directory
   38 | #include <ft2build.h>
      |          ^~~~~~~~~~~~

/usr/include/c++/9/pstl/parallel_backend_tbb.h:28:2: error: #error  Intel(R) Threading Building Blocks 2018 is required; older versions are  not supported.
   28 | #error Intel(R) Threading Building Blocks 2018 is required; older versions are not supported.
      |  ^~~~~

OK, so I need to know 


[LIST]
[*]exactly what to do about the "capstone library being in a bit of disarray".
[*]Will the versions of gtfw3 and gtk3+3.0 in the Ubuntu repository for 20.04 LTS work?
[*]Same for freetype.
[*]Will loading the Intel Threaded Building Blocks installer ([https://www.intel.com/content/www/us...options=online]("https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html?operatingsystem=linux&distributions=webdownload&options=online")) break Ubuntu?
[/LIST]


Thanks.

---

### Post by John Nagle on 2022-02-03
Got it built. All the needed packages are in the Ubuntu 20.04 LTS distro and once all the dependencies are installed, it works. No need to pull anything from external repositories.

---

