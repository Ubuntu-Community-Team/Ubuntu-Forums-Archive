---
title: "Problems with Grub with Fakeraid and Dual boot Win7/Ubuntu"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by Makenni on 2013-05-29
Hi and thanks in advance for any help with this problem.

I am a first time linux user attempting to install Ubuntu as a dual boot with Win7.  I have a fakeraid raid0 setup, which I understand makes things difficult from the get go.  The installation disks (12.04), even the alternate, all failed to successfully install grub.  

After many failed attempts at a successful installation following the advice of various other threads in which people had difficulty with raid0, I followed the advice on [this thread]("http://ubuntuforums.org/showthread.php?t=2052568"), which at first appeared to successfully install grub to my raid array.

Upon restart, however, I never reached the grub boot menu, instead finding myself on the [grub prompt]("https://fedoraproject.org/wiki/GRUB_2#Encountering_the_dreaded_GRUB_2_boot_prompt").  From there, the only success I've had is figuring out that I can boot to windows 7 fine using:

grub> set root=(hd0,msdos1)
grub> chainloader +1
grub> boot

I am very new to this, and quite frankly have no idea how to get the grub menu working or to boot into my ubuntu install.

Some relevant info: my Ubuntu install is a logical partition located at (hd0,msdos5).  I have a live cd that I can boot to, so I have terminal access.

Thanks for any help, and ask all the questions I wasn't smart enough to answer from the start.

---

### Post by Makenni on 2013-05-29
And then boot repair worked.  Thanks boot repair.  Stop looking at me like I'm retarded.  :P


PS: how do I change the tag to [Solved]?

---

