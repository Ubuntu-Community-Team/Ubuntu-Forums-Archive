---
title: "how would i remove ubuntu from a dual boot windows 7 machine?"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by agingric on 2010-11-20
hello all,

i have been out of the ubuntu loop for several months due to a motherboard problem.  i am going to be getting a new 64 laptop for christmas, with a dual core intel processor and windows 7 home premium as the OS.  

i am looking forward to having my own computer again will be installing ubuntu on it.  but, before i install ubuntu, i would like to know how to remove ubuntu and return the new computer to its original state if it ever becomes necessary.  

i was comforatable using programs such as mbrfix along with gparted to accomplish this task with my old computer, but that was a 32 bit windows xp machine.  

will i be able to use these programs with my new laptop?  i'm unfamiliar with 64 bit systems, windows 7 etc. and how they may differ from the older computer that i was used to.

thanks for any advice you may have.  

andy g

---

### Post by northern lights on 2010-11-20
Same thing.

Wipe the Ubuntu partition and add the newly created unallocated space to some existing Windows partition.

32 or 64 bit, Windows 98 or 7 - it's all ntfs.

---

### Post by galactica48 on 2010-11-21
> **northern lights said:**
> Same thing.

Wipe the Ubuntu partition and add the newly created unallocated space to some existing Windows partition.

32 or 64 bit, Windows 98 or 7 - it's all ntfs.

This action will not remove the grub installed in the MBR and every time you power on the computer you will get the Grub Menu.
You should remove the Grub Menu from the MBR or reinstall Windows 7 to factory default.
You can restore the MBR from Windows CD if you have it.

---

### Post by wilee-nilee on 2010-11-21
First reload the MBR with the MS bootloader, here is a recovery cd link and the command to run.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Run the highlighted command.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

You can then remove the Ubuntu if it is a dual boot with the disc manger in W7. **Some think a wubi is a dual boot so this is a little confusing.**

---

