---
title: "grub2 error on linux kernel load"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-09-04
I ran an update earlier today, and when I rebooted, I get an error on loading any kind of Linux kernel (I can chainload into Windows just fine though) and when I try to run memtest it tells me that I can't run the command:
linux memtest86.bin
and to try linux16. I try linux16 and it works just fine.
Right now I am running a livecd, I will reboot and post the exact error messages in a few minutes.

---

### Post by camper365 on 2009-09-04
Okay, here's the exact error:

> 
Out of range pointer 0x400040
Aborted - Press any key to exit
Broadcom UNDI PXE-2.1 v7.7.5
Copyright (C) 2000-2004 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All Rights Reserved

Broadcom Base Code PXE-2.1 v1.0.1
Copyright (C) 2000-2004 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-EC8: !PXE structure was not found in UNDI driver code segment


I think the BIOS is most of the error, but I posted the rest of it just in case.

---

### Post by setherd on 2009-09-04
try this thread. several others have had the problem
[http://ubuntuforums.org/showthread.php?p=7898113](http://ubuntuforums.org/showthread.php?p=7898113)

---

### Post by camper365 on 2009-09-04
I went to a livecd and ran a chroot, and did some package removal and reinstallation and eventually got to the point where I completely deleted the grub directory. After a while of installing and running commands, and a long while of sitting and staring at a booting livecd, it works beautifully now.

---

