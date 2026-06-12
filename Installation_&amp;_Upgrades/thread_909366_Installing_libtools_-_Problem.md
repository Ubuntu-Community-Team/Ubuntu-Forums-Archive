---
title: "Installing libtools - Problem"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by teddybouch on 2008-09-03
forgive me if any of this is confusing. I'm still relatively new to Ubuntu and a mechanical engineer. I just upgraded to Hardy Heron last night, and I am trying to install the libtool library in response to the following message that I got when trying to use a cmake to install another program:

-- Checking for libtool
CMake Error at libstage/CMakeLists.txt:6 (message):
  libtool library not found, aborting

I tried using sudo apt-get install libtool, and it says that it installed libtool, but when I go back and try the cmake command again, I get the same error. Please help - this is for my research and I am on a time crunch. Thank you very much.

---

### Post by teddybouch on 2008-09-03
Well, after looking through the list of all the packages that exist for Hardy Heron and installing them one at a time, it finally worked. Unfortunately, now my problem is in FLTK. I can run the cmake command without a problem, and it generates my make files. However, when I try the make command next, I get two errors:

[  2%] Building CXX object libstage/CMakeFiles/stage.dir/worldgui.o
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc: In static member function ‘static void Stg::StgWorldGui::fileLoadCb(Fl_Widget*, void*)’:
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc:409: error: ‘class Fl_File_Chooser’ has no member named ‘ok_label’
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc: In member function ‘bool Stg::StgWorldGui::saveAsDialog()’:
/home/abouchard/Desktop/Stage-3.0.1-Source/libstage/worldgui.cc:600: error: ‘class Fl_File_Chooser’ has no member named ‘ok_label’
make[2]: *** [libstage/CMakeFiles/stage.dir/worldgui.o] Error 1
make[1]: *** [libstage/CMakeFiles/stage.dir/all] Error 2
make: *** [all] Error 2

I've tried installing all the packages for FLTK again, but for whatever reason, it doesn't seem to find this ok_label file. Any suggestions? Please?

---

### Post by chikin03 on 2008-09-06
I am having problems which may be related to libtool as well.  Apparently there is an inconsistency between major versions, to the point that you simply have to use an old version of libtool whenever that's what the code was made for.  Or something.  Here's my code:

```
Dave@googlybox:~/workrave/workrave/trunk$ make
make  all-recursive
make[1]: Entering directory `/home/Dave/workrave/workrave/trunk'
Making all in intl
make[2]: Entering directory `/home/Dave/workrave/workrave/trunk/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/Dave/workrave/workrave/trunk/intl'
Making all in m4
make[2]: Entering directory `/home/Dave/workrave/workrave/trunk/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/Dave/workrave/workrave/trunk/m4'
Making all in po
make[2]: Entering directory `/home/Dave/workrave/workrave/trunk/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/Dave/workrave/workrave/trunk/po'
Making all in common
make[2]: Entering directory `/home/Dave/workrave/workrave/trunk/common'
Making all in include
make[3]: Entering directory `/home/Dave/workrave/workrave/trunk/common/include'
Making all in unix
make[4]: Entering directory `/home/Dave/workrave/workrave/trunk/common/include/unix'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/include/unix'
Making all in win32
make[4]: Entering directory `/home/Dave/workrave/workrave/trunk/common/include/win32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/include/win32'
make[4]: Entering directory `/home/Dave/workrave/workrave/trunk/common/include'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/include'
make[3]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/include'
Making all in src
make[3]: Entering directory `/home/Dave/workrave/workrave/trunk/common/src'
Making all in win32
make[4]: Entering directory `/home/Dave/workrave/workrave/trunk/common/src/win32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/src/win32'
Making all in unix
make[4]: Entering directory `/home/Dave/workrave/workrave/trunk/common/src/unix'
/bin/bash ../../../libtool --tag=CC   --mode=link gcc  -g -O2 -O0 -g -Wall -DGLIBCXX_FORCE_NEW -DGLIBCPP_FORCE_NEW  -g -o libworkrave-common-unix.la    
../../../libtool: line 838: X--tag=CC: command not found
../../../libtool: line 871: libtool: ignoring unknown tag : command not found
../../../libtool: line 838: X--mode=link: command not found
../../../libtool: line 1005: *** Warning: inferring the mode of operation is deprecated.: command not found
../../../libtool: line 1006: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../../../libtool: line 2250: X-g: command not found
../../../libtool: line 2250: X-O2: command not found
../../../libtool: line 2250: X-O0: command not found
../../../libtool: line 2250: X-g: command not found
../../../libtool: line 2250: X-Wall: command not found
../../../libtool: line 2250: X-DGLIBCXX_FORCE_NEW: command not found
../../../libtool: line 2250: X-DGLIBCPP_FORCE_NEW: command not found
../../../libtool: line 2250: X-g: command not found
../../../libtool: line 2419: Xlibworkrave-common-unix.la: command not found
X: user not authorized to run the X server, aborting.
../../../libtool: line 2431: Xlibworkrave-common-unix.la: command not found
../../../libtool: line 3575: libtool: link: libtool library `libworkrave-common-unix.la' must begin with `lib': command not found
../../../libtool: line 3576: Try `libtool --help --mode=link' for more information.: command not found
make[4]: *** [libworkrave-common-unix.la] Error 1
make[4]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/src/unix'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/Dave/workrave/workrave/trunk/common/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/Dave/workrave/workrave/trunk/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/Dave/workrave/workrave/trunk'
make: *** [all] Error 2

```

This was on make, after running an autogen.sh
The claim above about libtool versions was discovered after reviewing the quoted code, and searching for the first error in google.  I guess I will be watching for replies...

---

### Post by chikin03 on 2008-09-06
and.... this link seems to have fixed it.

[http://www.mail-archive.com/libtool@gnu.org/msg10248.html](http://www.mail-archive.com/libtool@gnu.org/msg10248.html)

---

