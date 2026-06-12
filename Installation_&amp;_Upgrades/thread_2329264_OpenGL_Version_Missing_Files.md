---
title: "OpenGL Version Missing Files?"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by sbbjpm on 2016-06-29
[TABLE]
[TR]
[TD="class: votecell"][CENTER][COLOR=#6A737C]wn vote
[/COLOR][favorite]("http://askubuntu.com/questions/792467/should-glcorearb-h-be-added-locally-or-in-system-level-include#")```

[/CENTER]
[/TD]
[TD="class: postcell"]I am running Ubuntu 12.04 and believe that I have the current version of OpenGL installed. When I run the following command in bash:
[CODE]glxinfo | grep "OpenGL version"
```
I get OpenGL version string: 4.4.0 NVIDIA 340.96.
My issue is that I am trying to build a 3rd party application that needs OpenGL, specifically the header "glcorearb.h", see [here]("https://github.com/libigl/libigl/issues/241") and [here]("https://www.opengl.org/registry/"). However, this file is not included with the other header files located in "/usr/include/GL" from the installed OpenGL package.

[LIST=1]
[*]Am I missing something in terms of the OpenGL package installation?
[*]If not, should I add the glcorearb.h file to the system wide installation or just include it locally in the 3rd party application?
[/LIST]
**Note:** I have tried both options of adding the file to the system and locally and the application builds fine either way. However, there are run time seg faults, which might be a related issue to the current OpenGL installed. The author of the 3rd party library does not see these seg fault issues on Fedora 24, where the glcorearb.h was present.[/TD]
[/TR]
[/TABLE]

---

### Post by sbbjpm on 2016-06-29
Two quick updates, I had a typo and am actually running 14.04.  Additionally, I have updated my NVIDIA driver to the newest version results of code snippet above are now: OpenGL version string: 4.5.0 NVIDIA 367.27.

---

### Post by ubfan1 on 2016-06-29
The file is actually in package mesa-common-dev, is that installed?  Use apt-file search glcorearb.h  to find all packages containing the file

---

### Post by steeldriver on 2016-06-29
Iin 14.04, it appears to be provided by the [mesa-common-dev-lts-wily](http://packages.ubuntu.com/trusty-updates/mesa-common-dev-lts-wily) package from the trusty-updates repository

Whether it is advisable to install that package I don't know - I don't really "get" all these lts update packages

---

### Post by sbbjpm on 2016-06-29
I can confirm that it is in the mesa-common-dev-lts-wily package.  When I try to install that package, it wants to remove:

libgl1-mesa-dev libglew-dev libglu1-mesa-dev libqt4-opengl-dev libqt5opengl5-dev mesa-common-dev qt5-default qtbase5-dev qtdeclarative5-dev ubuntu-desktop xorg xserver-xorg

I quickly said no to installing as the packages that need to be removed makes me nervous.

---

### Post by sbbjpm on 2016-06-29
For reference to the seg fault issue, which may or may not be related, I added the header file to the directory manually.  This allows the 3rd party application to build, but upon running a simple test with valgrind, I get the following seg fault callback.  

Jump to the invalid address stated on the next line
==13570==    at 0x0: ???
==13570==    by 0x5F09290: init (dlerror.c:177)
==13570==    by 0x5F096D6: _dlerror_run (in /lib/x86_64-linux-gnu/libdl-2.19.so)
==13570==    by 0x5F09197: dlsym (dlsym.c:70)
==13570==    by 0x6368304: ??? (in /usr/lib/nvidia-367/libGLdispatch.so.0)
==13570==    by 0x6368728: ??? (in /usr/lib/nvidia-367/libGLdispatch.so.0)
==13570==    by 0x40100CC: call_init.part.0 (dl-init.c:64)
==13570==    by 0x40101F2: call_init (dl-init.c:36)
==13570==    by 0x40101F2: _dl_init (dl-init.c:126)
==13570==    by 0x4001309: ??? (in /lib/x86_64-linux-gnu/ld-2.19.so)
==13570==  Address 0x0 is not stack'd, malloc'd or (recently) free'd

This same code ran fine on the author of the 3rd party library's Fedora 24 machine.

---

