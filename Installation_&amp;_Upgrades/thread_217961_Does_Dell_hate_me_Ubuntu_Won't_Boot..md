---
title: "Does Dell hate me? Ubuntu Won't Boot."
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Darkangel14615 on 2006-07-17
I just got my new Ubuntu 6.06 CDs in the mail today.

I'm quite excited as I put the CD in the drive and start up my computer, I select Start or Install Ubuntu, and alas; I can't even get to the Live CD version. It gives me one of 2 errors:

1 is a "<0> Kernel Panic: Failure to synch..." (or something of the sort)
2 is a "<1> Failure..." (of some sort, it says it can correct it but a reboot is needed. (Not quite sure what a reboot would do for a live CD...)) at either one the startup simply freezes. Can anyone help? I've had other Dell systems fail with other linux distros, but all of them always worked with Ubuntu no problem, this computer doesn't seem to like ANY of them. Computer Specs are as follows:

Dell Dimension 2350
1 Pentium 4 processor @ 2.2GHz
512MB Kensington RAM
nVidia GeForce4 MX 4000 (128MB)
Intel AC'97 Integrated Audio
Intel Integrated Video (not sure what model)
Dell 1024x768 15" Flatscreen LCD Display

I'm guessing the problem could be because I have both the integrated and the nVidia graphics cards, but then, I'm not any sort of expert by any means. I'd appreciate any help I could get, I really want to check out this new Ubuntu

---

### Post by tuxcantfly on 2006-07-18
the dapper kernel doesn't like your hardware. maybe try the development version of edgy? (it has a newer kernel that might work better)

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by tuxcantfly on 2006-07-18
the failed to sync error is usually about the harddrive or cd. do you have any other spare cd drives or harddrives that you could try out?

---

### Post by Darkangel14615 on 2006-07-18
well I have another CD drive, but it's USB, would it still work?

Oh, and I'd try the other image, but I'm afraid I have no blank CDs :(

Also, I took a closer look at the failed to synch error, it says it  couldn't write the VFS on unknown sector 8,1 I believe. That makes it my HD, doesnt it =\

Wait, I thought live CDs put everything on RAM, could it be having a problem with that? Perhaps a boot parameter I should change?

---

### Post by tuxcantfly on 2006-07-18
how about you just remove your harddrive, and make your cd the primary master drive?

---

