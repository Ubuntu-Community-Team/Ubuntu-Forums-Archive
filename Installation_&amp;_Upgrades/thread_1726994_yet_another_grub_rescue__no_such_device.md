---
title: "yet another: grub rescue / no such device"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by ralbach on 2011-04-11
My apologies in advance given the frequency at which this thread seems to occur.

The scenario:

Used Dell computer - no windows disk

3 HDDs

2 with windows XP (lets call them S <Seagate> and M <Maxtor>

1 with Ubuntu

GRUB menu used to come up but suddenly

my HDD w Ubuntu has died a clankerous death

NOW the No Such Device xxxxx     and    grub rescue

I've rearranged and booted w all the living Windows disks. If the S drive is present i get the grub rescue message. If the M drive is alone then the box says everything is missing and it gets no further.

I have a Live Ubuntu boot CD.

I've used it to boot the box and explore S.

Alas there is no evidence that I can see of grub anywhere and I cannot force grub to operate either.

an LS under RESCUE gives me:

(hd0) (hd0,msdos1) (fd0)

SET under RESCUE gives me:

prefix_(hd0,msdos1) /boot/grub
root=hd0,msdos1

from the under the Live Ubuntu boot CD

sudo fdisk -l

disk /dev/sda: 40Gb
...lots of hard disk data...

Device Boot    Start    End    Blocks     Id    System
/dev/sda1 *    1       4865     39079091   7     HPFS/NTFS

I've tried various other commands and such but GRUB just does not appear to be available.

So I'm a bit desperate and the good wife is rather angry as there are some important tax documents on that windows partition and tax day is coming and sadness is desending.

Thanks in advance,

-Robert

---

### Post by oldfred on 2011-04-11
This will tell us what is installed where. You may have to add which is Segate & which is Maxtor, or it may not matter.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

You can make most windows repairs from an Ubuntu liveCD, except for chkdsk. You need a windows liveCD to run chkdsk. If you do not have a XP disk, then download one of these. They are not really good at repairing XP, but can run chkdsk on any NTFS partition.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by rosencrantz on 2011-04-11
Erm, I'm a bit confused, correct me if I'm wrong.
You have a PC with two NTFS partitions (M and S), but no Windows system installed, and Ubuntu as the only installed OS on a third disk (let's call it U), which recently has died a horrible death and is inaccessible.
Grub Stage 1 seems to be installed in S's boot sector, as removing S gives you a generic BIOS message.
Now you want to a) install a new Grub and b) get at some files on one of the NTFS disks.
ad a) Without any operating system on the machine, you can't install Grub (even though there are some remnants on S's boot sector). You need a working linux to install the rest of it.
ad b) You can mount NTFS partitions from an Ubuntu Live CD, as well as edit and copy files. If you need an emergency non-live Ubuntu to work with them, and you have no free partition ready, try installing to a USB drive (if your computer can boot from USB). Or, if you have not too large amounts of data, you could move the data on M to S (or vice versa) and install Ubuntu on it.

If I misunderstood you and you wanted to access a Windows system install, try either a SuperGrub disk or the Recovery Console on a Windows XP installation CD.
FIXMBR (Windows CD) will wipe the aforementioned Grub Stage 1 on S, but I don't see what you'd want with it if Ubuntu is gone anyway...

---

### Post by ralbach on 2011-04-12
When my Ubuntu HDD was alive I would get a GRUB boot option to either boot into Ubuntu or Windows. Both would work. Both were formerly the resident "native" OS HDD for their respective former homes.

I do not know which of the 2 Windows based HDDs I was booting into. I wish I had documented that actually.

Now the Ubuntu disk is gone.

I simply want to get the Windows HDDs operable again. If I could have Ubuntu then great but it is not critical for me.

I did try to do an install from the Ubuntu Live disk. The first time I tried I had an option to install Ubuntu onto the HDD that also housed Windows. For some reason that failed. Since then that option of a side by side install has not been presented as an option

I now have the  rescatux 0.25 disk.

Using this I can see my Windows HDD which is identified as:

40 GB FILESYSTEM

it has a directory called

BOOT

which has a single subdirectory called

GRUB

That subdirectory has 189 items the majority of which are identified as Amiga Sound Tracker Audio <no I don't think they are>

many of these are what I have read as GRUB files such as chain.mod configfile.mod all of which are unreadable.

There are also img files and some riles such of .lst form that are editable.

That is where I stand this evening.

All thoughts and suggestions welcomed. Will try to run the script suggested earlier and post somehow.

thanks again

-Robert

> **rosencrantz said:**
> Erm, I'm a bit confused, correct me if I'm wrong.
You have a PC with two NTFS partitions (M and S), but no Windows system installed, and Ubuntu as the only installed OS on a third disk (let's call it U), which recently has died a horrible death and is inaccessible.
Grub Stage 1 seems to be installed in S's boot sector, as removing S gives you a generic BIOS message.
Now you want to a) install a new Grub and b) get at some files on one of the NTFS disks.
ad a) Without any operating system on the machine, you can't install Grub (even though there are some remnants on S's boot sector). You need a working linux to install the rest of it.
ad b) You can mount NTFS partitions from an Ubuntu Live CD, as well as edit and copy files. If you need an emergency non-live Ubuntu to work with them, and you have no free partition ready, try installing to a USB drive (if your computer can boot from USB). Or, if you have not too large amounts of data, you could move the data on M to S (or vice versa) and install Ubuntu on it.

If I misunderstood you and you wanted to access a Windows system install, try either a SuperGrub disk or the Recovery Console on a Windows XP installation CD.
FIXMBR (Windows CD) will wipe the aforementioned Grub Stage 1 on S, but I don't see what you'd want with it if Ubuntu is gone anyway...

---

### Post by ralbach on 2011-04-12
oops - in the first paragraph when I referred to "both were the native" I was referring to the two Windows HDDs.

Apologies

---

### Post by ralbach on 2011-04-12
Thanks for the guidance. Here is the results of the command. BTW I'm enjoying myself despite the sword of Damocles wielded by my wife and the IRS.

-Robert



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0608542E08541ECD                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /live/image              iso9660    (ro,noatime)
/dev/sda1        /media/0608542E08541ECD  ntfs       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177)
/dev/loop0       /media/disk              squashfs   (ro,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
```


> **oldfred said:**
> This will tell us what is installed where. You may have to add which is Segate & which is Maxtor, or it may not matter.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

You can make most windows repairs from an Ubuntu liveCD, except for chkdsk. You need a windows liveCD to run chkdsk. If you do not have a XP disk, then download one of these. They are not really good at repairing XP, but can run chkdsk on any NTFS partition.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by oldfred on 2011-04-12
You need to reinstall the windows boot loader to the MBR and remove grub from windows root. You also have two sets of some of windows boot files.

=> [COLOR=Red]Grub 2 is installed in the MBR of /dev/sda[/COLOR] and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: __________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini [COLOR=Red]/BOOT.INI[/COLOR] /ntldr [COLOR=Red]/NTLDR[/COLOR] [COLOR=Red]/NTDETECT.COM[/COLOR] 
                       /ntdetect.com [COLOR=Red]/boot/grub/core.img

[COLOR=Black]How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[/COLOR][/COLOR]From the windows XP repair CD:
FIXMBR  C:  #do not run if you still want grub in the MBR

---

### Post by ralbach on 2011-04-13
SOLVED!

I found an XP reinstallation CD and was able to run the fixes.

Thanks so very much everybody.

-Robert

---

