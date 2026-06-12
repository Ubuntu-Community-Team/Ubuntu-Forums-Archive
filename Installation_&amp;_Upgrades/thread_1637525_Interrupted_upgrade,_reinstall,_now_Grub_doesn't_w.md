---
title: "Interrupted upgrade, reinstall, now Grub doesn't work"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Trevor Burton on 2010-12-04
Hello everyone, I am in a mess.

Had a working WinXp/Karmic dual boot system
Tried to upgrade Karmic to Lucid and my daughter rebooted the system during the upgrade
I decided to do a fresh install of ubuntu, leaving Windows in place and it succeeded until the end when it said it could install the bootloader, so I proceeded without

[COLOR="Red"]Edit: I meant to say "it said it [COLOR="blue"]couldn't[/COLOR] install the bootloader, so I proceeded without.[/COLOR]

On booting, Grub drops to the command line.
I get grub>, not grub-rescue>
I did ls in grub and it showed the partitions I expected

/sda5 is /boot
/sda6 is /swap
/sda7 is /
/sda8 is /home

I tried to follow the grub2 command line manual by entering
```

set root=(hd0,7) (success)
linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda7 ro (failed - couldn't find file)

```
so I'm now a bit stuck.

Here are my bootinfo_script results
(by the way, sdb is just an e-SATA hard disc with nothing installed on it, I don't know why bootinfo thinks Windows is there.  Windows is on /sda2 with some sort of backup/recovery partition on /sda1)

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 397263670 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  1b Hidden W95 FAT32
/dev/sda2    *     16,370,235   387,471,734   371,101,500   7 HPFS/NTFS
/dev/sda3         387,473,406   625,141,759   237,668,354   5 Extended
/dev/sda5         387,473,408   387,676,159       202,752  83 Linux
/dev/sda6         387,678,208   396,064,767     8,386,560  82 Linux swap / Solaris
/dev/sda7         396,066,816   458,979,327    62,912,512  83 Linux
/dev/sda8         458,981,376   625,141,759   166,160,384  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        44D7-70B8                              vfat       BACKUP                        
/dev/sda2        4A38F4AD38F498E1                       ntfs       HDD                           
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3360563b-d9f2-49cd-b2d8-5e940dffd602   ext4                                     
/dev/sda6        a802ec63-61fe-4196-99d6-93d3adc55f7a   swap                                     
/dev/sda7        49017298-36c8-4545-9ad4-cf33ce252549   ext4                                     
/dev/sda8        15c85799-332f-47af-b367-c4cd40d12597   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6EDEDBBFDEDB7E31                       ntfs       Elrond                        
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..."

================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=================== sda5: Location of files loaded by Grub: ===================


 198.4GB: initrd.img-2.6.32-24-generic
 198.4GB: vmlinuz-2.6.32-24-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=3360563b-d9f2-49cd-b2d8-5e940dffd602 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=15c85799-332f-47af-b367-c4cd40d12597 /home           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 233.5GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

Any ideas?

Thanks

---

### Post by ronparent on 2010-12-04
The code you entered at the grub prompt was in error according to your results.txt. Your kernel is actually located in your /boot on sda5 (also known in grub 2 terms as (hd0,5)). I personally see no reason for a separate boot partition unless you have installed to a software raid or LVM partition. In any event no /boot/grub/grub.cfg was found. Without that file there is no grub menu. I would normally suggest reinstalling grub. In your case you could probably best reinstall 10.04 with only the separate /home (no formating of course) and the /. If you are sure that your /boot contains all the /boot system files you need to boot you could try a grub 2 reinstall. Use this reference ([https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2) to tell you how. I believe your root designation (which you mount to /mnt) would be your /boot partition. Let us know if you have any problems. Good luck.

---

### Post by drs305 on 2010-12-04
Edited:

You don't have a grub.cfg file. You can chroot into your Ubuntu installation and reinstall grub-pc. See the G2-Chroot link in my signature line. 

The method of reinstalling Ubuntu via LiveCd as mentioned by ronparent will also work but make sure you don't format anything!

---

### Post by drs305 on 2010-12-04
**Added:**
If your files are otherwise intact, I can probably give you the grub prompt commands to boot if you would prefer to do it that way.

**Further Added:**
Upon further review, I don't think you will be able to boot from the grub prompt. In addition to not having a grub.cfg file (which isn't needed for a boot from the prompt), the core.img file which should be in /boot/grub is located in your main partition. I don't know how it got there. 

It's possible that moving core.img back to /boot/grub from a LiveCD would work, but possibly not. A more certain approach would be to purge/reinstall Grub via the 'chroot' method. Make sure you mount both sda7 (/) and sda5 (/boot) before you enter the chroot. It's explained in the guide. The guide doesn't cover it, but you should also mount your /home partition as well.

---

### Post by ToFue on 2010-12-05
> **ronparent said:**
> ... I personally see no reason for a separate boot partition unless you have installed to a software raid or LVM partition. 

I do it to play with grub, modules & kernels from windows as ext2, using ext2.dll in windows (though others claim it read/writes ext3, it never did for me)

Trevor: I suppose you've gotten it worked out by now, but lemme say that I second drs305 and the others- LiveCD, then chroot then the grub installation method suggested by the other guys... after all, it's a complete new system install, minus grub. If you would have let the install happen, it would have went fine, configuring the chainloader for the windows boot entry automatically.. 

ronparent's link to the grub 2 guide is a great guide that helped me out before!

Also, I would venture that there's no grub.cfg file b/c grub hadn't completed a sucessful boot- that the file gets rewritten to whatever the last successful config was, and editing it would be pointless.. (just a guess)

also check out ```
$ info grub
```
And don't forget to check ownerships/permissions of your old /home once you're up with the new system ;)

---

### Post by Trevor Burton on 2010-12-05
Thanks everyone for the responses.

I chickened out of configuring/reinstalling grub and did a reinstall of Ubuntu but with just partitions for /swap, /home and /.

Then it booted up perfectly.

Not sure why the install didn't like a separate /boot partition, (I don't think I did anything else differently).

Unfortunately, Lucid is far less responsive on my gui than Karmic was - it takes around 3 seconds to show shortcut menus for example and dragging windows is virtually impossible (I drag and drop and wait for the window to follow some seconds later) - however, that is a different problem, so I'll make a new thread.

I think the message of all this is
1) don't let anyone near your computer during an upgrade
2) ? don't specify a separate /boot partition as the installer seems to have troubles (well, maybe, at least it did for me)

Thanks all, Trevor

---

### Post by ToFue on 2010-12-29
Lol Those are lessons I take to heart!

Out of curiosity of the lag issue, how big is your swap? If it's 8Gb like your earlier post suggests you've attempted, it may be too large.  It's possible that the system is read/writing to swap for everything it can before shoving to RAM for the quick execution...

As a test to rule this out is in the code frame; bassically turn swap off, check things out, then if that's not it then turn swap back on and snoop elsewhere.  If the lag Does improve then you'll probably have to rethink the size of your swap partition & shrink it

First see what partition swap is. For me, it was /dev/sda5, just replace with what fdisk tells you it is:

```


$ sudo fdisk -l


```

Then turn off the swap:

```


$ sudo swapoff /dev/sda5


```

Now check things out in gnome- see if the lag went away

To turn swap back on:

```


$ sudo swapon /dev/sda5


```


Ideally (for personal 'puter) you want no more than 2Gb of swap space before the benefit of swap becomes moot. I believe the rule of thumb is that you want twice the amount for Swap as you do for RAM except to not exceed 2Gb. So if you have 500Mb RAM, you'd set up 1Gb Swap; 1G RAM:2G.....

Without getting really into it, the Swap's function was to compensate for a lack of RAM. With today's computers allowing 4+ Gb of ram, the need for swap becomes less meaningful, but still important for the swap functionality provided by application being designed with swap in mind such as the hibernate power-down feature..

---

### Post by Trevor Burton on 2010-12-30
> **ToFue said:**
> 

...

Out of curiosity of the lag issue, how big is your swap? If it's 8Gb like your earlier post suggests you've attempted, it may be too large.

....

Thanks for that ToFue,  I think I did reduce the swap size when I reinstalled actually, but to 4Gb.  However, the slowness was due to a bug in Lucid to do with kernel mode setting which I believe was introduced in Lucid - I've disabled kernel mode setting and now graphics are working at normal speed.

Here's the reference from
[wiki.ubuntu.com]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

Trevor

---

