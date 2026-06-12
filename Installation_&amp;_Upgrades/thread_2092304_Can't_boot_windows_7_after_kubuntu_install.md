---
title: "Can't boot windows 7 after kubuntu install"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by vonforum on 2012-12-07
So, I have three hard drives. The first used to have windows xp on it, the second has two partitions, one containing just data and another containing windows 7 and the third is just data. I installed kubuntu to the first hard drive (replacing everything on it) with LVM. After doing this, my computer booted straight into kubuntu and I couldn't (even when selecting the second hard drive with F10 when starting my computer) boot into windows 7. So, I did the boot-repair (first output is at paste.ubuntu.com/1415312). Then tried all the os-prober (which returned absolutely nothing) and update-grub things. update-grub output:
```
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic

```So, finally, I had GRUB when I booted my computer, but still no Windows 7. So, after a bunch of messing around, I added some code to /etc/grub.d/40_custom, knowing that my windows should be at (hd1,1) (I lost the code, though, for now, so I can't really try again). So, after booting into grub and selecting windows 7, I finally made some progress as I now got the "bootmgr is missing" message. Since I don't have my windows 7 install cd, I had to use my windows 7 rc install cd, which I though may be good enough. It didn't detect that I had windows installed, so I tried what I found online, but "bootrec /fixboot" told me that it didn't recognise the filesystem or something, "bootrec /fixmbr" said operation completed. After this, grub broke again. So, from the kubuntu live cd, I installed grub again, got back into kubuntu. Grub has now lost windows 7, though, and I'm still unsure whether I can even boot into it.

Output from fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b68a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6aa5ac8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1341202589   670601263+   7  HPFS/NTFS/exFAT
/dev/sdb2   *  1341202590  1465144064    61970737+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0fada385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1465145343   732571648    7  HPFS/NTFS/exFAT

Disk /dev/mapper/kubuntu-root: 158.7 GB, 158708269056 bytes
255 heads, 63 sectors/track, 19295 cylinders, total 309977088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/kubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/kubuntu-swap_1: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/kubuntu-swap_1 doesn't contain a valid partition table
```And the output from a second run (which I did only a few minutes ago) of boot-repair at paste.ubuntu.com/1416875

And so far, os-prober returns nothing and update-grub still gives the same thing.

EDIT: Oh, and I noticed people talking about there being two boot folders (Boot and boot) in the windows drive, but mine has none. There is a Boot folder inside the Windows folder, but I'm not even sure about the legitimacy of that one.

---

### Post by oldfred on 2012-12-07
I do not know LVM as I do not reorganize partitions enough to want the extra level of complexity. And it does not add much to small drives, used more for large RAID drives on servers.

But Windows 7 normally installs to two partitions. I has a small 100MB boot/repair and the main install. But if you have another Windows already installed it will install its boot files into that install instead of the boot partition. Or if you have BIOS set to boot from sda and Install Windows to sdb, it will put the 100MB boot partition in sda. 
So I think you overwrote the boot files in sda.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
    
       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

    
You have boot flag on sdb2 and it had winload.exe which is normally the main install so it should be repairable. But you do not have a lot of space in it. Windows really likes 30% free.
You can repair your install in sdb2. I would set BIOS to boot from sdb, so it installs its boot loader to sdb, leaving grub's boot loader in sda. Change back to sda in BIOS after Windows is repaired.

I did see one user just copy bootmgr & the BCD folder to his install from the repairCD/USB and then edit BCD as it obviously was not for his install.

       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

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
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

