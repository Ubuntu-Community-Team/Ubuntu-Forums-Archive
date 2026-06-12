---
title: "fakeraid 9.1 upgrade; need help with Grub2"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Marco7 on 2009-11-25
Can anyone tell me how I should go about upgrading to and activating grub2 from within a fakeraid set-up, Karmic?

I upgraded from 9.04, but I'm still booting from Grub 1.5 and I think it's causing some problems.

Also I heard that 9.1 supports fakeraid.  Might I just burn an install Cd and reinstall the grub?

Please help.

---

### Post by Marco7 on 2009-11-25
More Information:

I tried to follow this guide [(http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)]("http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html"), but apparently I already have grub 2 installed.

```
~$ sudo apt-get install grub2


Reading package lists... Done

Building dependency tree       

Reading state information... Done

grub2 is already the newest version.

The following packages were automatically installed and are no longer required:

  libswscale-unstripped-0 libqt4-test libamrnb3 libqt4-xmlpatterns libqt4-help

  libavcodec-unstripped-52 libamrwb3 libpostproc-unstripped-51 qt4-qtconfig

  libqt4-assistant gtk2-engines-ubuntulooks libavformat-unstripped-52

  binutils-static libavutil-unstripped-49

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2 not fully installed or removed.

After this operation, 0B of additional disk space will be used.

Setting up grub-pc (1.97~beta4-1ubuntu4) ...

Generating core.img

grub-probe: error: no mapping exists for `nvidia_aaicbcde3'

Auto-detection of a filesystem module failed.

Please specify the module with the option `--modules' explicitly.

dpkg: error processing grub-pc (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of grub2:

 grub2 depends on grub-pc; however:

  Package grub-pc is not configured yet.

dpkg: error processing grub2 (--configure):

 dependency problems - leaving unconfigured

No apport report written because the error message indicates its a followup error from a previous failure.

                          Errors were encountered while processing:

 grub-pc

 grub2

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The Error: no mapping exists for `nvidia_aaicbcde3'

This is my root drive, it is third in line on my hard drive, and grub 1 is still working on it.

Does this help, can anyone see what is going on here???

---

### Post by gilson585 on 2009-12-21
i have posted instructions here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) basiclly you revert to grub1 since grub2 doesnt support fakeraid as of yet

---

