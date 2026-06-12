---
title: "Dual boot Windows and Ubuntu - *but* with Ubuntu already installed on a separate hard"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by lyhy on 2011-01-25
Hi,

I just bought a new Windows 7 machine and want to install Ubuntu 10.10 for a dual boot environment. There's a lot of info describing how to do this, but it all describes re-partioning the Windows drive, burning Ubuntu on a CD, inserting that CD, etc.

I had a dual-boot Windows and Ubuntu machine that just died on me. Windows was on one hard drive and Ubuntu - along with my entire software development environment - was on the other. As far as I know both drives are fine.

When my new (Windows) machine gets here I want to open it up and stick in the Ubuntu hard drive from my old machine... but then I'm not sure what to do. I'd really like to be able to boot to that hard drive (or the Windows one), just like I did before. 

It seems that this should be simpler than installing a fresh Ubuntu from a special CD, after all, everything is already expanded and working on the hard drive. Can someone give me some pointers that will help me solve this problem? 

Thanks,
Larry

---

### Post by buntudawg on 2011-01-25
Hi Larry

You should just be able to install your Ubuntu HDD, set bios to boot from that drive and then run```
sudo update-grub
``` to find the Windows OS.

---

### Post by oldfred on 2011-01-25
If you installed custom video drivers, then you may have to uninstall them. Otherwise it should be just as buntudawg said, plug it in and boot it from BIOS.

---

### Post by lyhy on 2011-01-27
Thanks for the replies! Really, they are much appreciated and clear up a lot of my confusion. My new machine should arrive next week and then I can try this stuff out.

Thanks again,
Larry

---

