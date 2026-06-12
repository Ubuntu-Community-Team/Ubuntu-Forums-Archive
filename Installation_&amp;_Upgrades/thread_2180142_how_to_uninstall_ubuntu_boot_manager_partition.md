---
title: "how to uninstall ubuntu boot manager partition"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by Eric_G. on 2013-10-11
Curious to know if there is a way I can uninstall my Ubuntu boot manager partition from my HDD.  I want to run Ubuntu from CD-ROM instead of from my HDD and I can't seem to find a way of deleting the boot manager partition.  It is dual boot (Ubuntu V13.04 and Windows 7) and I want to boot straight into Win7.  Thank you.  :)

---

### Post by oldfred on 2013-10-11
IF a BIOS based system with a full partition install (not wubi), you just need to install a Windows or Windows work alike boot loader to the MBR.

You can use Windows and its command fixMBR, or Boot-Repair, or manually from a liveCD.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

You will still have the Ubuntu partition on your hard drive.

If wubi you need to use Windows editBCD to remove the boot entry.

---

### Post by Eric_G. on 2013-10-12
Thank you much.  I will give it a try.  /Eric

---

