---
title: "Disk boot failure"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by mnox on 2007-12-26
Hello.

I have a problem with dual boot. I use GRUB to boot ubuntu and vista. It was fine until today. Now i receive a message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". Is there a way to fix this without formating the hard disk drive and installing both systems again?

---

### Post by benrboone on 2007-12-26
Have you made any changes recently to your windows or ubuntu systems?
If not can you use your live cd and see the partitions on the computer

---

### Post by mnox on 2007-12-26
No changes. And I can see all partitions on the liveCD.

---

### Post by Pumalite on 2007-12-26
I think your drive went south. I hope not. You can try reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You can try restoring the Windows MBR with you Installation CD>Recovery>FIXMBR>FIXBOOT.
If nothing works, use TestDisk:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by mnox on 2007-12-26
Reinstalling Grub didn't work and Windows can't even see an existing installation, so i couldn't restore MBR. I'll try TestDisk now.

---

