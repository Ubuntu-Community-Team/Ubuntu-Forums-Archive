---
title: "libarkrpg2 problems"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by kiwibird on 2005-10-14
I'm getting this problem while trying to upgrade:
/var/cache/apt/archives/libarkrpgc2_0.1.4b-6ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libArk.so.0.1.0', which is also in package libarkrpg
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I'm sure there's more behind it, but there was so much stuff that just whizzed right past my eyes while installing, and this one seemed to stand out. Anyone know what I have to do? Can I just sort of... move that libArk.so.0.1.0-file out of the way for dpkg so that it'll stop complaining and let me get breezing?

(also, anyone know what if the Norwegian language pack is nb or no?)

Fuller output (after running dist-upgrade a couple times):

```
kiwibird@kiwishiba:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  arkrpg: Depends: libarkrpgc2 but it is not installed
  lsb: Depends: lsb-graphics but it is not installed
       Depends: lsb-cxx but it is not installed
  ubuntu-base: Depends: ubuntu-minimal but it is not installed
               Depends: ubuntu-standard but it is not installed
  x-window-system-core: Depends: libgl1-mesa-dri but it is not installed
E: Unmet dependencies. Try using -f.
kiwibird@kiwishiba:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools libarkrpgc2 libgl1-mesa-dri lsb-cxx lsb-graphics lvm2 ubuntu-minimal ubuntu-standard
The following NEW packages will be installed:
  initramfs-tools libarkrpgc2 libgl1-mesa-dri lsb-cxx lsb-graphics ubuntu-minimal ubuntu-standard
The following packages will be upgraded:
  lvm2
1 upgraded, 7 newly installed, 0 to remove and 564 not upgraded.
783 not fully installed or removed.
Need to get 0B/13.6MB of archives.
After unpacking 38.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "no_NO.UTF-8",
        LC_ALL = (unset),
        LANG = "no_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
Setting up diff (2.8.1-11ubuntu1) ...
(Reading database ... 171977 files and directories currently installed.)
Unpacking libarkrpgc2 (from .../libarkrpgc2_0.1.4b-6ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libarkrpgc2_0.1.4b-6ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libArk.so.0.1.0', which is also in package libarkrpg
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace lvm2 2.00.32-1 (using .../lvm2_2.01.04-5ubuntu1_i386.deb) ...
Unpacking replacement lvm2 ...
Selecting previously deselected package initramfs-tools.
Unpacking initramfs-tools (from .../initramfs-tools_0.32_all.deb) ...
Selecting previously deselected package ubuntu-minimal.
Unpacking ubuntu-minimal (from .../ubuntu-minimal_0.80_i386.deb) ...
Selecting previously deselected package ubuntu-standard.
Unpacking ubuntu-standard (from .../ubuntu-standard_0.80_i386.deb) ...
Selecting previously deselected package libgl1-mesa-dri.
Unpacking libgl1-mesa-dri (from .../libgl1-mesa-dri_6.3.2-0ubuntu6_i386.deb) ...
Selecting previously deselected package lsb-graphics.
Unpacking lsb-graphics (from .../lsb-graphics_3.0-1ubuntu8_i386.deb) ...
Selecting previously deselected package lsb-cxx.
Unpacking lsb-cxx (from .../lsb-cxx_3.0-1ubuntu8_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libarkrpgc2_0.1.4b-6ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TSJason on 2005-11-16
-Bump-

 I also ran into this problem during a dist-upgrade from hoary to breezy.

---

