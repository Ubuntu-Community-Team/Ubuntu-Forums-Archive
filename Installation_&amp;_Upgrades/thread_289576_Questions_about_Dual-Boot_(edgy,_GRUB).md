---
title: "Questions about Dual-Boot (edgy, GRUB)"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by jgio on 2006-10-31
Hello to everyone!

I 'm John from Greece a CS student. I have the following problem:

I have **3** **separate** HDDs 2 Sata & 1 IDE. Sata1 the WindowsXP, Sata 2 is empty(where i 'll install linux) and the IDE is a spare with data (music, video etc.). My **Plan is GRUB with Ubutnu in SATA2, SATA1 with XP(as it is) & spare as it is**. Last night i tried to install Ubuntu Edgy from the alternative CD & when the installer asked where did i want to install GRUB i chose not in **MBR** and wrote **"/dev/sdb"** the installer continued-> reboot, i log into BIOS change the boot sequence and put sata2 as the first drive, restart again GRub loaded ok, i selected Ubuntu 2.6...mpla mpla, and then nothing loaded just an **Error 17** about mount selected partition. Also Windows didn't load from Grub i got **NTLDR is missing**...

Any help...??
thnx in adv

---

### Post by Rhubarb on 2006-10-31
I think when you change the boot sequence in the BIOS you actually change where the computer thinks the drives are.
So you should specify grub to point to /dev/sda to get Ubuntu to start.
Windows would now be in the sdb drive.

You shouldn't need the alternative CD to do this, just install as normal to sda.  If you're feeling paranoid, disconnect your windows hard disk temporarily while installing.

---

### Post by jgio on 2006-10-31
Thnx i ll try it later in the evening ;)

---

