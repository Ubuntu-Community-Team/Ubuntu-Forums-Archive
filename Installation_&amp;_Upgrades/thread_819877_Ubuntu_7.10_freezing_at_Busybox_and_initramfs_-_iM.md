---
title: "Ubuntu 7.10 freezing at Busybox and initramfs - iMac G3/400"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by boejucci on 2008-06-05
i'm brand new to Ubuntu and Linux in general so bear with me on this one. i have an old iMac G3/400 running OS 9 and i'm trying to get Gusty onto it. i typed in "live-nosplash-powerpc" at start up (because simply putting "live" or "live video=ofonly" either shut down or froze on a black screen) but it hits Busybox and initramfs and "enter help for a list of commands..."

i don't know what to do! i'm using an alternate disk (i guess that obvious) and i'm trying to erase OS 9 and replace it with 7.10.

any help??



joey.


also: would any of you out there suggest i use a different version of *buntu? i'm into recording and what not and a friend is going to help me dual boot Ubuntu Studio on my MacBook, but i have no idea what would be best for this old iMac.

---

### Post by avtolle on 2008-06-06
Try this: at the busybox prompt, type "sudo modprobe ide-core", then when the prompt reappears, "exit" (without the quotation marks, of course, in both cases). This should allow you to continue the booting process. If it does, then there is a way to make it permanent, but I'm without my notes right now. If you will look in the Forum Archive for Apple PPC Users (I think that's the name) you will find some additional help.

I'm on a G4 Cube, running 8.04 ppc version. There are some issues with this, too, involving editing the /etc/X11/xorg.conf file, but for now, try the above; and, join us on the Apple Users Forum.

---

### Post by avtolle on 2008-06-06
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) is something that may be helpful to you as well.

---

