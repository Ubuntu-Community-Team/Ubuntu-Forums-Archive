---
title: "FIX for NVidia 375.39 on Ubuntu 17.04 Mate"
date: 2017-04-30
forum: Installation &amp; Upgrades
---

### Post by eatpancakes on 2017-04-30
after using
 ```
sudo apt-get install emacs
```
on install I get an error
```
/usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link
/usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link
```

same error when using
```
sudo apt-get install r-base
*blah blah blah*
/usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link
/usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link
```

I got the fix from here
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860)

[B]TL;DR

[/B]ANY NEW INSTALLATION OF UBUNTU 17.04 MATE WITH PROPRIETARY NVIDIA DRIVER 375.39 WILL REQUIRE THIS SCRIPT TO FIX INSTALL ERRORS. THERE ARE OTHER WAYS TO FIX IT AS THIS METHOD MAY NOT BE THE BEST. BUT IT WORKS. PROVIDED WITH NO WARRANTY

```
#!/bin/bash
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.39 /usr/lib/nvidia-375/libEGL.so.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.39 /usr/lib32/nvidia-375/libEGL.so.1
```

you may need to uninstall the apps you installed and reinstall them after running the fix

```
sudo apt-get remove application
sudo apt-get install application
```

where "application" is replaced with the name of your desired package to install

mods & maintainers perhaps this problem could be corrected upstream for a more automatic bulletproof proprietary nvidia driver installer.

if there is anything incorrect in my post please say so. if you think this is dangerous please edit my post as necessary to prevent damage to other users.

---

### Post by jwatte on 2017-09-09
I considered doing the same fix, but the installed file is not just a plain duplicate of the driver:

```
jwatte@ripper:/usr/lib32/nvidia-375$ ls -l libEGL*
lrwxrwxrwx 1 root root     23 Jul 24 14:00 libEGL_nvidia.so.0 -> libEGL_nvidia.so.375.82
-rw-r--r-- 1 root root 724168 Jul 19 22:04 libEGL_nvidia.so.375.82
lrwxrwxrwx 1 root root     11 Jul 24 14:00 libEGL.so -> libEGL.so.1
-rw-r--r-- 1 root root  61404 Jul 19 20:27 libEGL.so.1
-rw-r--r-- 1 root root  15012 Jul 19 20:27 libEGL.so.375.82

```

I think a correct solution would be to understand why they're different, first.

The symbols that are in the bigger file but not in the smaller are:
```
+eglClientWaitSync
+eglCreateImage
+eglCreatePlatformPixmapSurface
+eglCreatePlatformWindowSurface
+eglCreateSync
+eglDestroyImage
+eglDestroySync
+eglGetPlatformDisplay
+eglGetSyncAttrib
+eglWaitSync

```

It may also be that the implementation is different of the symbols that are implemented.

A safer solution to shut up ldconfig would be:

```
#!/bin/bash
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.1.1 /usr/lib32/nvidia-375/libEGL.so.1
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.1
sudo ln -s /usr/lib/nvidia-375/libEGL.so.1.1 /usr/lib/nvidia-375/libEGL.so.1

```

Also, note that these error messages, while annoying, are warnings, not errors -- they don't prevent anything from working as far as I can tell.

---

