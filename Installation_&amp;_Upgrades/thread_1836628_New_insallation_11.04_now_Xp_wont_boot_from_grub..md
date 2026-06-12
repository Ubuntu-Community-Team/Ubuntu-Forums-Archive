---
title: "New insallation 11.04 now Xp wont boot from grub."
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Rockling on 2011-08-31
Ok So my original pc had Windows XP and an older version of Ubuntu.
I had also an old 10g hard drive in the PC which when i removed windows would not boot up. So the brainwave I had was remove the 10g hardrive and install Ubuntu 11.04 as dule boot with XP.
The problem is first when booting it says secondary hard drive missing press F1 to continue or F2 for system setup.
When I press F1 it loads the grub 1.99 and lists Ubuntu 11.04 and XP.
If i select Ubuntu it works but if i select XP it goes blank for a few seconds and then brings back up the grub menu.

Below is the result of the  Boot Info Script. Any help would be greatly appreciated.

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 260164594 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   253,987,649   253,907,325   7 NTFS / exFAT / HPFS
/dev/sda3         306,198,900   312,496,379     6,297,480  82 Linux swap / Solaris
/dev/sda4         253,987,650   306,198,899    52,211,250  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D5-0A17                              vfat       DellUtility
/dev/sda2        902099C32099B0A8                       ntfs       
/dev/sda3        3ca23b3f-386e-4ddb-993e-84a3a3c86789   swap       
/dev/sda4        e6c84b80-bcf2-4577-9a8f-41bb7b1adde0   ext2       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext2       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems] 
```

---

### Post by OakRaider4Life on 2011-08-31
Try running

```
sudo update-grub
```

from Ubuntu then rebooting.

---

### Post by Rockling on 2011-08-31
> **OakRaider4Life said:**
> Try running

```
sudo update-grub
```

from Ubuntu then rebooting.


Hi Oak

Already tried that with no luck.

Thanks

---

### Post by OakRaider4Life on 2011-08-31
Then that about exhausts the limit of my expertise on this subject :/

---

### Post by oldfred on 2011-08-31
You installed grub's boot loader to the Windows boot partition PBR. Windows has to have its boot code in the PBR.

> sda2: ______________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   [COLOR=Red]Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 260164594 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

From a windows CD it is the fixBoot command, but the above is just restoring the backup that window has in NTFS partitions.

---

### Post by Quackers on 2011-08-31
At some time grub has been installed to your Windows XP partition. Windows doesn't like grub in there so it refuses to boot.
If you boot into Ubuntu and navigate to the root of Windows XP you will see a folder called boot. There may be a second folder Boot, or there may not be.
In either of those folders there will be a folder called boot with another folder called grub within it.
Delete those folders BUT NOT the original boot folder!
If you are unsure post a screenshot of the boot folder's contents in your next post.

EDIT or see oldfred's post above, which will over-write the grub folder :-)

---

### Post by Rockling on 2011-08-31
Thanks Olfred, Quackers

After using testdisk as suggested from

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

My PC boots straight into Windows XP
andthe results from Boot Info Script is

                ```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

```

I have now booted up into Ubuntu by using Super Grub 1.98 disk
and selected Any OS from the menu.
I will try a sudo update-grub from here and let ye know how i got on.

---

### Post by oldfred on 2011-08-31
The reason you get to grub at all is that you actually are using the grub installed in the windows partition that overwrote the windows code. Grub2 then works as the windows boot loader jumps to the partition with the boot flag and loads the code in that PBR. Since it is grub not windows grub does work. 

You also need to install grub2's boot loader to the MBR so you have a choice of which to boot. Your results.txt does not show a grub.cfg menu. Are you getting a menu when you boot? If so you can just reinstall the boot loader, otherwise you may need to chroot into your system and totally reinstall grub2.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda4 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda4 if not correct:
sudo fdisk -l
#confirm that linux is sda4
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by oldfred on 2011-08-31
I should have had you do this first since from Ubuntu it is easy to reinstall grub2's boot loader to the MBR. If you can boot with supergrub this also works. You can run either of the two commands in red. I think the second (dpkg) is like a full install of grub so it automatically runs the update-grub.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda  then just run:
[COLOR=Red]sudo grub-install /dev/sda[/COLOR]
sudo update-grub

Second way:
#to get grub to remember where to reinstall on updates:
[COLOR=Red]sudo dpkg-reconfigure grub-pc[/COLOR]
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Rockling on 2011-08-31
> **oldfred said:**
> 
#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda  then just run:
[COLOR=Red]sudo grub-install /dev/sda[/COLOR]
sudo update-grub



Your a star Oldfred 
The above worked for me
Thanks

---

