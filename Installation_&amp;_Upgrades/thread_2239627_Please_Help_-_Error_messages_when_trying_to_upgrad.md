---
title: "Please Help - Error messages when trying to upgrade to 14.04 LTS"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2014-08-14
Folks,

While attempting to upgrade to version 14.04 LTS the following occurs.

Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you still want to continue with the upgrade?

The above URL shows the following:
When updating your system with Update Manager, you will see a warning if your machine does not have*3D support for running the unity desktop environment. This could happen for several reasons:
Outdated hardware not providing required level of OpenGL support
Too new hardware without driver support yet
Obscure hardware without 3d support
Virtual machines
Binary drivers required but not installed
If you choose to continue anyway, Ubuntu will try to run using software rendering (via LLVMpipe). While llvmpipe is pretty good on modern CPUs, if your video card is old your CPU is likely old too, and it may result in unusable performance.
Alternatives may include sticking with an old ubuntu release or switching to one of the lighter weight derivatives or Debian. For 12.04 and 12.10, ubuntu-classic (no effects) is also a feasible option. To do this, install the gnome-session-fallback package, and then on the login screen click the gear icon and select "Ubuntu-classic (no effects)".

I would like to be able to install the new version but I don't know what I can do to fix the problem as I haven't a clue what any of the information above means. 

The current version is 12.04.4 LTS with all the latest updates.

My system is less that a year old. It has an AMD chip and 8GB of memory and more than adequate disk space to accommodate a new version.

I have no idea which 'Graphics Hardware' is installed and don't even know how to find out.

Please help

Regards,

Bob

---

### Post by grahammechanical on 2014-08-14
There are two commands to run

```
ubuntu-drivers device
```

That will give information about your graphic adapter and the various video drivers available for it. This, second command will tell if your graphic adapter can run Unity 3D

```
/usr/lib/nux/unity_support_test -p
```

This is what I see when I run that command

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.5


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


You could try going on the machine's manufacturer web site and looking up the specifications. 

Regards.

---

### Post by bobmac on 2014-08-14
Many thanks for your quick reply. However, when I enter your commands this is what I get!

$ ubuntu-drivers device
ubuntu-drivers: command not found

/usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

---

