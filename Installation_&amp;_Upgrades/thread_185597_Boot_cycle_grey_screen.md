---
title: "Boot cycle grey screen"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by godard on 2006-06-01
This has been a problem for me for the *entire* Dapper cycle of releases and i'm stumped that no one else has come across this with a similar configuration. RC1, RC2 and Flight 7 are unable to get through the boot process.   They get through the initial couple of textual screens "Loading ramdisk" etc and then a grey screen appears which locks up the system. I filed a bug on this some time ago (it got categorized as a yaboot problem, but i'm not entirely convinced it might not be a graphics issue, it appears the monitor is trying to change screen resolution to me and getting stuck) but sadly the problem persists. 

[https://launchpad.net/distros/ubuntu/+source/yaboot/+bug/42305](https://launchpad.net/distros/ubuntu/+source/yaboot/+bug/42305)

Yesterday i ran through a clean install of breezy and a dist-upgrade using the Fight 7 CD and then updating to all of the latest packages through another dist-upgrade. The system was entirely usable, but upon reboot i get stuck at the same grey screen again. I'm going a bit nuts - there's a working install of dapper in there i just can't get to it. Any advice?

---

### Post by nkbj on 2006-06-01
When you get past the "loading ramdisk" it's not yaboot. I think you are right it could be graphics. What happens if you do <ctrl><alt><grey-minus> or <ctrl><alt><grey-plus> when you hit the grey screen? (grey-minus and grey-plus are the + and - keys on the numerical keyboard). These key combinations should cycle through different screen resolutions.

Another thing to try is to do <ctrl><alt><F2> at the grey screen. If you get a command prompt try **dpkg-reconfigure xserver-xorg** and reboot.

---

### Post by nicolas314 on 2006-06-01
I am experiencing the same trouble here: iMac G4 (ppc) 800Mhz
Install from Breezy works fine, dist-upgrade Ok, first reboot Ok.
I did not get a console at that point, but had to wait until X was
started to see something on screen.

Next reboot: black screen with a couple of lines (loading init or sth like
that) and then nothing. It is definitely not related to X. The kernel crashes
before it goes any further, I get it is related to video mode settings in
the booting kernel.

---

### Post by nkbj on 2006-06-01
Your problems look alot like this: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

---

### Post by godard on 2006-06-01
Many thanks for your help nkbj, i tried your suggestions and unfortunately there is no changing the monitor resolution. However i'm pretty sure the bug you linked to is the one i have. I've asked one of the contributors if he can give a step by step guide on resolving the problem (which appears to be kernel related), i think there might be more of us with this bug than i thought. Many thanks again.

---

### Post by phibxr on 2006-06-02
Yes, we are quite a few who are experiencing this bug. I've been hitting that bug report frequently for the last quarter, but now the bug has been assigned and a patch have been made which, hopefully, will be implementet in a coming kernel update.

---

### Post by nkbj on 2006-06-02
[QUOTE=godard]I've asked one of the contributors if he can give a step by step guide on resolving the problem...[/QUOTE]
I think the best way to solve the problem is to install breezy, wait for a kernel upgrade with the fix and then dist-upgrade to dapper. We can also hope that they release a cdrom iso with the fixed kernel.

Regards,
Niels Kristian

---

