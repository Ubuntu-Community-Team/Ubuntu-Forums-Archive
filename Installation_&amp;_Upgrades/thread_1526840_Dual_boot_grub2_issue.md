---
title: "Dual boot grub2 issue"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by JacKeown on 2010-07-08
Hi, today I installed Ubuntu on my laptop which already had Windows 7 on it...so now I'm dual booting...but when I go into grub it won't show Windows 7 anymore.  Does anyone know easily how to get Grub2 to show it?  I've looked in my grub.cfg file and there was no Windows entry and I wonder if and how I could use the 40_custom file to add Windows into Grub2... Thanks in advance!

---

### Post by Rubi1200 on 2010-07-08
Can you still boot into Windows?

From within Ubuntu:

```
sudo update-grub
```

If that doesn't work, post back here and we will try and take it from there.

---

### Post by JacKeown on 2010-07-08
> **Rubi1200 said:**
> Can you still boot into Windows?

From within Ubuntu:

```
sudo update-grub
```

If that doesn't work, post back here and we will try and take it from there.
No I can't get boot into windows because it's not showed it the bootloader...and also sudo update-grub gives this:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done


and when I reboot Windows still isn't there...

---

### Post by JacKeown on 2010-07-08
Ok...now I got it to show windows in grub2 by deleting a folder named boot in my windows partition because it was being confused with the Boot folder since it's case insensitive...but grub2 still won't load windows 7...it just sits at a blank screen with the blinking cursor in the upper left corner doing nothing forever...ugh...

---

### Post by lindsay7 on 2010-07-08
type sudo fdisk -l in the terminal (that is the lower case letter L) and then enter you password.  Post the results here.

---

### Post by JacKeown on 2010-07-08
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c213e83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         240     1927768+  27  Unknown
/dev/sda2   *         241       27307   217407665+   7  HPFS/NTFS
/dev/sda3           27307       30402    24862721    5  Extended
/dev/sda5           27307       30268    23786496   83  Linux
/dev/sda6           30268       30402     1075200   82  Linux swap / Solaris

---

### Post by oldfred on 2010-07-08
If you had the grub boot folder as well as the /Boot windows folder did you try installing grub to the windows partition.

this may be the fix, you can run the boot info script and check if grub is in the windows partition as shown.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

IF the above does not work or you need more help:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by JacKeown on 2010-07-08
I attached my RESULTS.txt file on here and with testdisk the 6th screen showed no BackupBS

---

### Post by oldfred on 2010-07-09
You have grub installed to windows boot sector. Windows has part of its boot code there.

sda2: _______
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector[/COLOR] of sda2 and 
                       looks at sector 447357120 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

You can try testdisk and the rebuild boot sector or use a windows 7 CD to repair the boot sector with fixboot. I list all the commands in case you need them.

Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
[COLOR=Red]BootRec.exe /FixBoot [/COLOR] #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

If you run fixMBR you will have to reinstall grub2 after getting windows working.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by JacKeown on 2010-07-10
Ok...so I've now tried all of that...I used bootrec /Scanos and it said it couldn't find any windows partitions...after trying bootrec /fixboot and fixmbr I rebooted and nothing would boot at all...it just sat at this blank black screen...so I went into my live cd of Ubuntu and reinstalled grub on my linux partition and I can now get into Ubuntu but still no Windows :(

---

### Post by oldfred on 2010-07-10
When you installed the windows boot loader to the MBR and could not boot that said windows was still broken. Also when it says it cannot find the windows partition it still is having issues.

Installing grub at that point will not fix windows, but does let you boot Ubuntu.:)

Did you run the chkdsk until there were no errors? 

You can also try the MFT repairs if that is a problem that chkdsk did not fix.
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by mjk3902 on 2010-07-10
I had the same problem.  If you have a windows reinstall disk, you can recover from this by booting to it, then run FIXBOOT.  Worked for me.

---

