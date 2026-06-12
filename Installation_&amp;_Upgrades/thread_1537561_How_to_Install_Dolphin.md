---
title: "How to Install Dolphin"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by jboywer on 2010-07-23
I downloaded the Dolphin Software(Wii & gamecube Emulator) i am wondering how do i install it. I notice i only see files, i dnt even know where to find the application after it is downloaded. Help!!

---

### Post by Potters Son on 2010-08-13
I have no idea.

When I downloaded Dolphin from the website, it came packaged as a .tar.bz file. I tried extracting it to a folder (I chose /opt, the same folder Google Chrome puts itself). But when I tried to run it, it had trouble finding the libraries:
```
user@hostname:/opt/dolphin-emu$ ./dolphin-emu 
20:00:874 Source/Core/Common/Src/FileUtil.cpp:92 W[COMMON]: IsDirectory: stat failed on ./user/Wii/title/00000001/00000002/content/: 
DL: Error loading DLL plugins/libPlugin_VideoOGL.so: libCg.so: cannot open shared object file: No such file or directory20:00:957 Source/Core/Common/Src/DynamicLibrary.cpp:88 E[COMMON]: DL: Error loading DLL plugins/libPlugin_VideoOGL.so: (null)
20:00:957 Source/Core/Core/Src/PluginManager.cpp:248 W[CONSOLE]: PluginInfo: plugins/libPlugin_VideoOGL.so is not a valid Dolphin plugin. Ignoring.
DL: Error loading DLL plugins/libPlugin_VideoSoftware.so: libGLEW.so.1.5: cannot open shared object file: No such file or directory20:00:975 Source/Core/Common/Src/DynamicLibrary.cpp:88 E[COMMON]: DL: Error loading DLL plugins/libPlugin_VideoSoftware.so: (null)
20:00:975 Source/Core/Core/Src/PluginManager.cpp:248 W[CONSOLE]: PluginInfo: plugins/libPlugin_VideoSoftware.so is not a valid Dolphin plugin. Ignoring.

```

---

### Post by linux18 on 2010-08-13
tar.gz, tgz, and tar.bz2 are source packages, you need required dependencies to compile them. I'll see what I can do about turning it into a deb, but it will be a 64-bit deb as I have a 64-bit system, for 32-bit I need to get my other system running.

---

### Post by Potters Son on 2010-08-13
Never mind. There's a PPA with prebuilt packages:

[http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages]("http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages")

---

### Post by jboywer on 2010-08-20
THank you Potters Son

---

