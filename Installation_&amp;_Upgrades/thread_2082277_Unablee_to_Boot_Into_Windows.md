---
title: "Unablee to Boot Into Windows"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by woody22075 on 2012-11-08
Here is the story: I installed Windows & on Drive A, and then installed Ubuntu on Drive B. Grub worked properly and I was able to dual boot.  I realized that I should have installed Windows on drive B (newer and bigger drive).  I copied the Windows partition (using Clonezilla) to drive B, overwriting the Ubuntu install and reinstalled Windows on a separate partition on Drive B.  I can boot into Ubuntu but not Windows (I think I deleted the Windows MBR).  Any ideas how I might recover from this?

Thanks!

Marshall

---

### Post by oldfred on 2012-11-08
Windows does not like changes. Its NTFS partition boot sector has to match drive's partition table. Therefore any clone should really be back to where it originally was to work correctly. Windows also seems to prefer to be on sda. And it needs to be the same location on the drive, which it seems you did not do. Did you put it into a primary partition with the boot flag? That is vital.

Have you tried Windows repairs? That may reset everything. 

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

