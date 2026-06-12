---
title: "Package configurations -- what are they?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2009-12-26
Hi, all:

For VTK (kitware) configuration, 
I met the following configuration things, 
which I need some clear explanation. Please do help


```

CMAKE_HP_PTHREADS                OFF   // what is HP_PTHREADS ??  It seems there are several types of pthreads.
CMAKE_USE_SPROC                  OFF   // yes, sorry, till now, I've got no idea what is SPROC ? 
                                       // what for? See this many times in various packages

FFMPEG_INCLUDE_DIR               FFMPEG_INCLUDE_DIR-NOTFOUND                
// using Ubuntu 9.10, it looks like VTK only supports FFMPEG <= 0.5. 
// the default FFMPEG in current Ubuntu 9.10 now doesn't afford an single "include" directory.

 FFMPEG_dc1394_LIBRARY            FFMPEG_dc1394_LIBRARY-NOTFOUND
 FFMPEG_dts_LIBRARY               FFMPEG_dts_LIBRARY-NOTFOUND
// why FFMPEG_dc1394 and FFMPEG_dts?  
I installed libdc1394-22-dev , 
but it seems this has nothing to do with FFMPEG ???

 MEMORYCHECK_COMMAND              MEMORYCHECK_COMMAND-NOTFOUND
// Couldn't find any package related to MEMORYCHECK ? which package is required for this package?

OPENGL_xmesa_INCLUDE_DIR         OPENGL_xmesa_INCLUDE_DIR-NOTFOUND
// strange tha under Ubuntu 9.10, this can not be found.
All mesa related packages have been installed including
libgl1-mesa-dev
libglu1-mesa-dev
libglw1-mesa-dev
libosmesa6-dev
mesa-common-dev
xlibmesa-gl-dev
xlibmesa-glu

Only except package "libgl1-mesa-swx11-dev". 
However, if I tick this up, package "ubuntu-desktop" will be removed, 
as well as some conflicted mesa packages listed above.
So, what is "OPENGL_xmesa_INCLUDE_DIR" for?


 LIBPROJ4_INCLUDE_DIR             LIBPROJ4_INCLUDE_DIR-NOTFOUND
 LIBPROJ4_LIBRARIES               LIBPROJ4_LIBRARIES-NOTFOUND
// In fact, I installed libproj-dev from current Ubuntu 9.10 repository. But,


 PROJ_LIST_EXTERNAL               OFF
 PROJ_USE_GSL                     OFF
 PROJ_USE_PTHREADS                OFF
// What are these three choices for? If I picked ON for any of the three, I will obtain the following error message:
 CMake Error at Utilities/vtklibproj4/CMakeLists.txt:28 (message):
   You may not define both PROJ_LIST_EXTERNAL and BUILD_SHARED_LIBS.  Turn one
   off and re-run CMake.
Therefore, it's better I turn off these 3 choices right?

 VERDICT_BUILD_DOC                OFF
 VERDICT_ENABLE_TESTING           OFF
 VERDICT_MANGLE                   ON
 VERDICT_MANGLE_PREFIX            vtk
 VERDICT_USE_FLOAT                OFF
// What are VERDICT for? Always meet this in many packages.  Something is even more strange. If I enable "VERDICT_ENABLE_TESTING           ON", after the configuration, it will be automatically change back to "VERDICT_ENABLE_TESTING           OFF" !!! Amazing.... The same thing happens to "VERDICT_USE_FLOAT   OFF" as well.

VLI_LIBRARY_FOR_VP1000           VLI_LIBRARY_FOR_VP1000-NOTFOUND
// what is this for? It seems nothing is related with this choice in Ubuntu 9.10?


 X11_XTest_LIB                    X11_XTest_LIB-NOTFOUND
 X11_Xaccessrules_INCLUDE_PATH    X11_Xaccessrules_INCLUDE_PATH-NOTFOUND
// Strange that in ubuntu 9.10, these 2 packages are not able to be found. What are these 2 packages for?



Finally, I really hope all VTK_  settings can be carefully explained 
because all these parameters are specifically for VTK !!
Here, I enumerate all I'm interested in as follows:

 VTK_LARGE_DATA_ROOT              VTK_LARGE_DATA_ROOT-NOTFOUND
// what is LARGE_DATA?  is it VTKData? My directory tree is just like
some folder
----------- VTK
----------- VTKData
How should I arrange these 2 directories "VTK" and "VTKData"?

VTK_LEGACY_REMOVE                OFF
 VTK_LEGACY_SILENT                OFF
// What are VTK_LEGACY for?

 VTK_OPENGL_HAS_OSMESA            OFF
// what is OSMESA? what's the relationship between opengl and osmesa?

 VTK_TESTING_USE_FPE              ON
// what does FPE refer to??
 VTK_TESTING_USE_LOCALE           OFF
// what does LOCALE refer to?

 VTK_USE_FFMPEG_ENCODER           OFF
// As you may see above, FFMPEG_INCLUDE_DIR    FFMPEG_INCLUDE_DIR-NOTFOUND , so it's better for me to turn off VTK_USE_FFMPEG_ENCODER  .

VTK_USE_MANGLED_MESA             OFF
// OPENGL_xmesa_INCLUDE_DIR         OPENGL_xmesa_INCLUDE_DIR-NOTFOUND , so it seems i'd better turn off VTK_USE_MANGLED_MESA

VTK_USE_MPEG2_ENCODER            OFF
// This seems to be specific for vtkmpeg2encode, right?
which one should be installed first? 
vtk or vtkmpeg2encode? 
why not afford a standard installation for vtkmpeg2encode?  
Or just integrate VTK and vtkmpeg2encode??

 VTK_USE_TDX                      ON
// What is TDX for?
 VTK_USE_TEXT_ANALYSIS            ON
// What is TEXT_ANALYSIS for?

 VTK_USE_VOLUMEPRO_1000           OFF
// What is VOLUMEPRO_1000?



```

Hope anybody can afford a detailed explanation on all the above VTK configuration settings.

Thank you very much.

Best Regards
JIA Pei

---

### Post by rCXer on 2009-12-26
Personally, I have never studied the parameters in detail. I have no idea what those do. Accepting the defaults have always worked for me. 

You can see short parameter descriptions using cmake's gui.  It is installed by...
```

sudo apt-get install cmake-gui

```
To start the gui go to Applications -> Programming -> CMake. Set the source and binary directories for vtk.  Click "configure" which after completion (if I remember correctly), should show all the parameters.  To see what a parameter does, hold your mouse cursor over its name.  A description should popup after a few seconds.

By the way, I like the website in your signature :)

---

### Post by ramsrom on 2012-07-27
If you don't have GUI (e.g only terminal as in server version).
Then just install ccmake which is more convenient (GUI-like) running in terminal.

sudo apt-get install cmake-curses-gui
ccmake <whatever CMakeLists.txt>

---

### Post by Elfy on 2012-07-27
Old thread closed.

---

