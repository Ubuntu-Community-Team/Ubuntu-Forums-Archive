---
title: "Help-GRUB and LILO won't install into /target/!"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by jerseyboy91 on 2007-03-06
Yesterday, I asked some people on the forums whether or not I should install Ubuntu or Xubuntu on a spare computer of mine. I decided to burn a copy of Xubuntu's alternative CD, just to play it safe. 

I can get through the hardware installation, but the software installation ends at 85 percent (when it says Cleaning Up), but the integrity check shows no problems with the CD that I burned. 

So I skipped the end of that step and just went ahead and tried to install GRUB. I get an error saying that GRUB failed to install into /target/. Then, I try installing LILO, and I get the same error.

I'm trying to make this a Linux-only computer (a first in my house), but there's lots of obstacles in the way right now.

Computer stats: 
Intel Celeron 566 MHZ processor
20 GB Hard Drive (wiped clean of Windows 98 and everything on the HDD)
128 MB RAM

I recall people talking about using fdisk to try and restore the original MBR, then trying to reinstall GRUB onto the MBR. Anyone know if that could help me fix this problem?

---

### Post by maikelc on 2007-03-12
I've had the same problem for GRUB (probably) and found a workaround that works for me:
Try installing without an Internet-connection....

---

