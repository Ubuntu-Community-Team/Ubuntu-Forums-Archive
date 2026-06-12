---
title: "Disk Controller install issues, add driver?"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by clabrown on 2010-07-14
Hello:

Is it possible to load additional disk controller drivers during installation ... like you could do on Windows NT during installation, or perhaps by modifying the kernel before installation?

I've got an IBM xSeries 206 (8242-1SU) with 2 internal SATA drives connected to the built in SATA controller, and several Adaptec 2610 6 port SATA cards that I wanted to use as a NAS unit. Originally I thought I'd try OpenFiler, that install seems to see the disks on the integrated controller but not on the 2610, and even let me configure LVM, but after install it won't boot, gets stuck at a "starting udev" prompt. 

To trouble shoot and as a reality check I thought I'd try installing Ubuntu because of it's "just works" compatibility reputation. I have several install CDs lying around and first tried Ubuntu 10.4. It does not detect any hard disks to install to at all. It also has video issues during the install where the non highlighted selections in several lists are unreadably light. 

Just for grins I tried a Kubuntu 8.10 CD. It had no problems with the integrated hard disk controller or the video. The installation proceeds without a hitch and the system boots up without error. However it does not see the 2610. So somewhere between 8.10 and 10.4 Ubuntu lost what ever driver is being used to talk to the integrated SATA controller.

I tried disabling the integrated controller and using just the 2610, but again it is not detected.

I remember several years ago (2006? 2007?) installing Ubuntu on a generic box with a 2610 6 port sata board without issue, but it seems that now 10.4, and 8.4 don't recognize it. I'm assuming that if my memory is correct, perhaps that driver was removed from the kernel sometime before version 8.10. So is it possible to put back both the drivers needed for the integrated controller as well as the 2610 in order to install to this machine?

Thanks.

---

### Post by cariboo on 2010-07-14
The Live CD has problems detecting SATA drives at times. Try the Alternate install CD, it's worked for me every time.

---

