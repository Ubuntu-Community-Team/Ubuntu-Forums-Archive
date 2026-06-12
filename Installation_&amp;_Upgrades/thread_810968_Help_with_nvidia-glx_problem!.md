---
title: "Help with nvidia-glx problem!"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by samus789 on 2008-05-28
I was trying to install sun-java5-jre through apt-get and this is what i got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 139408 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/libwfb.so' with
  different file `/usr/lib/nvidia/libwfb.so.xserver-xorg-core', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
ryan@ryan-desktop:~$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 12.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 139408 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/libwfb.so' with
  different file `/usr/lib/nvidia/libwfb.so.xserver-xorg-core', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)


can anyone help me? why is the Nvidia-glx getting in the way? i've got the newest nvidia driver, i even tried reinstalling after getting rid of the glx part of it in the xorg.conf, but that didn't help.

thanks in advance!

---

### Post by samus789 on 2008-06-07
Nevermind, i figured it out, i had to manually delete the conflicting GLX file and reinstall the nvidia driver.

---

### Post by ShadowWraith on 2008-06-19
I have the same problem! Can you elaborate on how you fixed it?

---

