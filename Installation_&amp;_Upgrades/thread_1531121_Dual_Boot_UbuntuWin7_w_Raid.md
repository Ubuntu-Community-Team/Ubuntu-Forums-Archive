---
title: "Dual Boot Ubuntu/Win7 w/ Raid"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by tigereyes1 on 2010-07-14
Good Day Everyone
 
I want to start by letting you know i'm kind of a newbie in regards to Ubuntu. I was fortunante enough to get it working on my computer for a couple months so i do know enough to get myself in trouble but not much more.
 
Here's my issue...
 
I want to dual boot Windows 7 with the new Ubuntu. The reason i havn't been able to get this to work is i've got a different set-up for my hard drives. I've got 3 hard drives. Drives 1 & 2 are set up with Raid 1 and boot windows. Drive 3 has Ubuntu installed. 
 
I initially installed Windows 7, install worked
I then installed Ubuntu, it worked fine but no longer booted to windows
I did a fdisk and it recognized the drives as being there but i'm assuming it was not booting because Grub didn't recognize the Raid? I'm not sure so any insight in to this issue us greatly appriciated
I still have Windows on drives 1 & 2 and Ubuntu on drive 3 but haven't booted in to Ubuntu after I restored the MBR to boot in to windows.

---

### Post by YesWeCan on 2010-07-14
Windows/Ubuntu bootloader conflicts are so common and cause such grief that I sometimes think Ubuntu install should not allow writing to a Windows HD at all.
My belt and braces recommendation is to physically disconnect your RAID drives. Then install Ubuntu 10.04/grub 2 (or reinstall grub 2) on the third disk. Then shutdown, reconnect the RAID drives and reboot into bios to set the Ubuntu HD as the first boot device. Boot Ubuntu and then run 'update-grub' in a terminal. This should add Windows to the grub menu.

---

### Post by tigereyes1 on 2010-07-15
Thanks for the advice. I'll give that a try when i get home from work today.

---

### Post by A Feyn Man on 2010-07-15
I am in a similar situation (except that I have a new Sony Vaio Z with 2 SSDs in RAID 0). I have Win7 installed and I resized that partition and created ~50GB of free space that I want to put Lucid on. I booted the live CD and everything is fine, but when I go to install it says that it fails to put the ext4 file system on the unallocated space.
If I go to the BIOS and disable RAID so that I can install Lucid, won't that pretty much kill my Win7?

---

### Post by tigereyes1 on 2010-07-16
Yeswecan, thank you very much! It worked. i'm so excited. thank you for the assistance.

---

