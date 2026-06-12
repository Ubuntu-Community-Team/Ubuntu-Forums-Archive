---
title: "Stage two of installation never started?"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by eBeL on 2006-07-01
Hey, I'm fairly new to Linux still, but have been messing around with it for a while.  I decided to install Ubuntu on my Windows box, so I added a hard drive I had lying around in the closet.  I popped in my newly created Dapper disk and formatted/installed Ubuntu on my second hard drive.  All seemed well and it asked me to remove the CD and reboot.  Surpisingly instead of bringing up the GRUB selection screen, it just continued into Windows.  Restarted again to make sure I just didn't miss it, again it booted into Windows.  I'm thinking I may have maybe pushed No when it prompted to install GRUB, but I'm pretty certain I installed it.  Any advice?

Thanks :)

---

### Post by Nonno Bassotto on 2006-07-01
You say you installed Ubuntu to your second hard drive; are you sure GRUB was installed to the MBR of the first hard drive? Otherwise your computer, at boot, just reads the first drive and launches Windows.
Try setting your BIOS to boot from the second hard drive and look if Ubuntu starts. In this case, you will have to manually install GRUB to the first drive. I don't remember how, sorry, try searching on the forum.

---

### Post by eBeL on 2006-07-02
Aha perfect.  I set the BIOS to read the second hard drive first, and GRUB loaded right up.  Thanks! :p

---

