---
title: "GRUB disappeared"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by jlumbtx on 2015-05-19
I have Win7 installed on one hard drive and Ubuntu on a 2nd.  I had problems with the Win7 and eventually did what MS calls a "Windows Upgrade In-place" which seems to be reinstalling the OS without losing all files as you would with a clean install.
It looks like I now have the most up-to-date Win 7 SP1 on my C drive.  But this process has cost me GRUB.
 
I have very few files on my Ubuntu drive so a clean install would not be a real loss.  Do you think GRUB would reappear if I reinstalled Ubuntu?
Or is there a way to install just GRUB?

John

---

### Post by oldfred on 2015-05-19
Grub's default install is to sda, which was the Windows drive.
And your major Windows update reinstalled its boot loader to sda.

Does your system let you boot from sdb? 
If so better to install grub to sdb and reset BIOS to boot sdb first.

You can reinstall grub to sdb (or sda) from live installer or many Linux repair CDs.

If you use Boot-Repair, do not run Auto Fix as that installs grub to all drives. You want to keep Windows boot loader on Windows drive and grub boot loader on Ubuntu drive.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

