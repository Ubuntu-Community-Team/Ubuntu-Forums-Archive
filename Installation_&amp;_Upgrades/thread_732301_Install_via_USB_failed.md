---
title: "Install via USB failed"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by dotancohen on 2008-03-22
I am trying to install Kubuntu 8.04 beta from USB. I have never attempted a USB install before, so I used this page as a guide:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

When I boot from USB I get the Kubuntu graphic with the following text:
"The default installation is suitable for most desktop or laptop systems. Press F1 for help and advanced installation options.

To install only the command-line base system, type 'cli' then ENTER. For the default installation, press ENTER."

Do I press enter, but I get this error message:
"could not find kernel image: /install./vm"

I googled the error, and the only hit was to the following thread on these forums:
[http://ubuntuforums.org/showthread.php?t=71567&page=3](http://ubuntuforums.org/showthread.php?t=71567&page=3)

The user DaBruGo posted some changes that he made to the syslinux.cfg file. I used his syslinux.cfg file, which suggests a kernel location of "vmlinuz" instead of"/install/vmlinuz", but got a rather similar error message:
"could not find kernel image: vmlinux"

While I have read many other threads about installing from USB, not many other people have this problem and I cannot find a solution. What must be done? Thanks in advance.

---

