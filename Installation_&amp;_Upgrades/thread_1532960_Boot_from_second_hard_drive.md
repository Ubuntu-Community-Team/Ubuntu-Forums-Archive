---
title: "Boot from second hard drive?"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-17
Is there an easy way to do this? I thought about copying my laptop hard drive to my internal TB hard drive, but I since I have a spare laptop HD anyway and my case has a slot for laptop HDDs I think I am just going to throw it into the case as a second hard drive.

How can I add that partition to the boot loader on my other hard drive without using RAID?

---

### Post by ajgreeny on 2010-07-17
If your BIOS recognises the disk without a problem and you are running a system with grub2, ie 9.10 or 10.04, unless you upgraded and kept legacy grub, all you need to do is run sudo update-grub and the new OS should be found and added to the grub menu.

Presumably the laptop disk will already have grub or grub2 on its own MBR so you could choose that disk from BIOS at boot up as first device and should go straight to that disk's OS.  Or at least I can't see why that wouldn't work.

---

### Post by C.S.Cameron on 2010-07-17
What Ajgreeny says has worked for me.

---

### Post by Nick_Jinn on 2010-07-18
> **ajgreeny said:**
> If your BIOS recognises the disk without a problem and you are running a system with grub2, ie 9.10 or 10.04, unless you upgraded and kept legacy grub, all you need to do is run sudo update-grub and the new OS should be found and added to the grub menu.

Presumably the laptop disk will already have grub or grub2 on its own MBR so you could choose that disk from BIOS at boot up as first device and should go straight to that disk's OS.  Or at least I can't see why that wouldn't work.

Thank you.

---

