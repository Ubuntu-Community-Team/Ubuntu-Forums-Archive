---
title: "error: no such device:"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by cmwittr on 2010-07-06
I had Vista installed on my internal hdd, and installed ubuntu 10.04 to my external usb hdd.  I decided that I didn't really want ubuntu anymore, so I just formatted my external. Well, GRUB decided to hang on my internal, and mess up my boot process.  I can't get to a boot menu to launch vista. How can I get windows bootloader back and get grub away?

---

### Post by oldfred on 2010-07-06
per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Or you can use the windows CD/DVD and run fixMBR.
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by cmwittr on 2010-07-06
Thanks So much.  The vista disk in recovery mode did the trick.  You're a saint.

---

