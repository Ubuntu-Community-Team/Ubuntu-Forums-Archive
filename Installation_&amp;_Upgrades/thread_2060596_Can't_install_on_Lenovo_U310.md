---
title: "Can't install on Lenovo U310"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by COLiNx86 on 2012-09-20
So, I recently got a Lenovo U310 and decided to dual boot on it.  I copy the 12.04 ISO to my flash drive, and proceed to installing Ubuntu.  After a few attempts I give up on dual booting, and just decided to go for a complete new install.  After around 5 more attempts, I have had no luck, and currently my computer just stops at a PXE-MOF screen and then restarts.  I currently have no idea whats wrong.  I was trying to install '/' and '/boot' and the swap on the 32gb SSD, and then have '/home' on the 500gb HD.  I tried typing in the  commmands, 
```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```But it didn't work.  I've tried going into the bios and turning off "Intel Rapid Start Technology", I've tried switching the harddrive/SSD to ACHI, I've tried not even using the SSD and only using the HD, but no luck there either. I feel like it's not installing grub or something.  At this point I'm out of ideas, and currently have a 700$ paperweight.  So, by chance, does anyone have any more ideas?  

Thanks,
Colin.
[B]
EDIT:  Solved it.[/B]

---

### Post by abufo on 2012-09-26
I have the same problem, how did you solve it?
Thanks,
Andi

---

### Post by COLiNx86 on 2012-09-27
I finally managed to get it by turning of iRST in the BIOS, switching the HD/SSD to ACHI, and then the last part that took me a while to figure out, once you're in your BIOS (Fn+F12 at boot) go over to the Boot tab and change the first option (UEFI) to disabled.

Just a warning, but the WiFi performance on this laptop and Ubuntu sucks.  I never had any issues with it on Windows 7, but on Ubuntu I'm lucky to get more than 56Kbps. :mad: Maybe someone knows a solution??
EDIT: I take that back..The download performance sucks.  I can browse the web and everything is okay (only okay, though), but whenever I try to download something I get awful performance.

---

### Post by snowz on 2012-11-18
I've read somewhere on the web that the WiFi got repaired on the **U310 **& **U410 **laptops produced in august 2012 or later.

---

