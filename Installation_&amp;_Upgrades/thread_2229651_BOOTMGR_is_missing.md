---
title: "BOOTMGR is missing"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by IAmTheElementX on 2014-06-14
Im working on building a home server out of an old desktop. I formatted the hard drive and installed ubuntu on it. When i boot i get BOOTMGR is missing. What do i do?

---

### Post by oldfred on 2014-06-14
You still have a Windows boot loader in the MBR, and it is trying to boot from the PBR or partition boot sector with the boot flag and find the Windows boot file bootmgr.

You need to have grub installed into the MBR of the hard drive that you are booting from with BIOS.
The server installer is not a live DVD or flash drive. You can manually install or use another live installer.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by IAmTheElementX on 2014-06-15
The problem when I was going to install grub was that the machine won't boot from a live disk. I tried liveUsb which wont boot. I booted with a PLOP and tried booting from usb there and it froze a few times. LiveDVD gives me a "reboot and select proper boot device"

---

### Post by oldfred on 2014-06-15
How did you install server version, from a DVD or flash drive? 
If a old system, you may need Lubuntu or other lightweight gui based system.

I think the Boot-Repair CD version is based on Lubuntu so it can work on older systems.

---

### Post by IAmTheElementX on 2014-06-15
I'm installing normal 32-bit ubuntu so i have a base OS. After that I was going to install freeNAS for my server. The PC is very old, 2006-ish. It's a piece of junk I got from my uncle, I have a bunch of hard drives and I was planning on popping them in and having a home server for storage and streaming. (PC is pathetic Pentium 4, 512mb RAM). I'm checking out Lubuntu to see if it runs better (I got a liveDVD to work and it runs awfully)

---

### Post by yancek on 2014-06-15
If you are trying to install the latest Ubuntu Desktop, you will have difficulty with it even if you manage to get it installed as the absolute minimum to run it is 512MB RAM.  Try a lighter distribution suggested above.

---

### Post by oldfred on 2014-06-15
You need Lubuntu as a liveDVD or flash drive as 512MB is not much. And full Ubuntu needs a far amount of RAM, but Unity also need an up to date video card or chip to handle it.
But that should be plenty for a server without a gui or a very light-weight one. Some install just the gui and not the full desktop with all its software.

---

