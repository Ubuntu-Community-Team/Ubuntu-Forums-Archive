---
title: "Post install - where did Ubuntu go?"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Doomspark on 2010-09-03
My computer (home-built) has 3 hard drives in it.  These are separate drives, not partitions. All are SATA.

500 gig - Windows 7
320 G - Ubuntu - sort of.  Was empty.
120 G - currently empty.

When I installed Ubuntu, I told it to install on the 320G drive and use the entire disk.  It wanted to install "side by side" on the same drive that has my Windows 7 install.  The install appeared to proceed normally, and I remember seeing a message go by that said it was doing something with grub.

On reboot, my system goes directly into Windows and doesn't give me any sort of option to launch Ubuntu instead. Windows no longer sees the 320 G drive, which makes me think that the install is there and what I have is some odd flavor of boot issue.

I'm VERY much a Linux / Ubuntu noob, so any advice on how to make this dual boot happen is muchly appreciated.

---

### Post by ronparent on 2010-09-03
Very likely the grub boot loader was written to the root of the drive you installed Ubuntu to. Your best bet is to change the drive boot order in your computers bios so that it looks to the 320G drive first. It also most likely added win7 to your grub menu, so once the boot loader finds grub you should be able to boot to Win 7 also.

---

### Post by Doomspark on 2010-09-06
Yep - that fixed it.

Thanks to all who read and helped out.

---

