---
title: "Dual boot problems..."
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by unyikabonya on 2011-11-30
Hi everyone,
I'm not entirely sure if i post this thread on the right website, but since i'm trying to solve my problems using ubuntu 10.04(Lucid Lynx), it might still be the right place.I wanted to set up a dual boot configuration on my computer(ubuntu and windows7), for which i already installed windows 7, but with the help of another hard drive(I borrowed it.), so the boot files are missing, and it's own boot repair couldn't fix it, because it didn't recognise the installation. I have installed ubuntu after this, and that one works fine, except I can't get it to recognise that windows partition and so I can't set up a dual boot configuration. I guess it could be solved by starting all over again, but i want to avoid that, if it's possible. To be exact, i want to avoid installing windows again, because i hat doing that, but if reinstalling ubuntu makes any difference, it's no problem...

---

### Post by darkod on 2011-11-30
No, reinstalling ubuntu won't help if windows boot files are missing. That's the problem with win7 asking you where to install but in some cases actually putting two of the boot files on another partition. Linux always puts them together.

Open your win7 partition from ubuntu, and take a look at the files. First look for:
bootmgr
Boot/BCD

Then look for:
Windows/System32/winload.exe

My guess is the first two are missing. Not sure if you copy them from another installation can help. In winXP it usually works if you have standard setup.

---

### Post by unyikabonya on 2011-11-30
Thanks for the quick reply.
I looked for the files you mentioned, and was very surpised to find all of them at their place...now i know these files are there, i really can't see why the windows boot recovery won't recognise it's installation...

---

### Post by Mark Phelps on 2011-11-30
Need more details ...

Do you have two separate physical drives?

If so, is Windows on one drive and Ubuntu on the other?

If so, have you tried having only one drive at a time connected, and then, can you boot both the Windows drive and the Ubuntu drive?

If you have Windows on its own drive and it's not booting, to repair with a Win7 CD or DVD, you often have to run Startup Repair three times -- ignoring any errors that you see.  It takes that many passes to completely repair the boot operation because that utility only finds and repairs one thing at a time.

IF you go through all that and the standalone Win7 drive still does not boot, then you may have a more serious problem with Win7.

---

### Post by darkod on 2011-11-30
Did you try running update-grub anyway?
Since you had two disks at one point, and now only one, maybe all you need to do is update the config. In terminal try running:
sudo update-grub

and see if that locates win7.

---

### Post by unyikabonya on 2011-11-30
No, I have only 1 drive with 3 partitions(one for windows/ntfs/, one for ubuntu/ext4/, and one for storage/fat32/). I tried updating grub before, made no difference.

---

### Post by Cavsfan on 2011-11-30
> **unyikabonya said:**
> No, I have only 1 drive with 3 partitions(one for windows/ntfs/, one for ubuntu/ext4/, and one for storage/fat32/). I tried updating grub before, made no difference.

You need 2 for Ubuntu 1 - EXT4 and one for swap - about 2048MB. You can have a max of 4 on a HD.

---

### Post by unyikabonya on 2011-11-30
Yep, i have a swap partition, just forgot to mention it...i also have a home partiton...

---

### Post by darkod on 2011-11-30
Ubuntu can function without a swap partition, no problem about that even if you didn't have one.

But your win7 seems messed up good. Even the windows repair process not discovering it is a sign of that too.

If you follow the link in my signature and run the boot info script as explained there, and post the results here it might show us more.

---

### Post by Cavsfan on 2011-11-30
> **unyikabonya said:**
> Yep, i have a swap partition, just forgot to mention it...i also have a home partiton...

That is good.

> **darkod said:**
> Ubuntu can function without a swap partition, no problem about that even if you didn't have one.

But your win7 seems messed up good. Even the windows repair process not discovering it is a sign of that too.

If you follow the link in my signature and run the boot info script as explained there, and post the results here it might show us more.

I did not know you could get by without a swap partition. 
**Darkod** knows a lot more than I about this and you will get much help after posting the results of that script.
You might want to give the tutorial in my sig. a look once you have your system dual booting again.
The tutorial is for dual booting and it's pretty extensive but, straight forward too.
It makes your GRUB2 screen look good and you never have to do anything to it after it is setup.
There are several examples of what it will look like.
Good Luck!

---

### Post by unyikabonya on 2011-12-01
> **darkod said:**
> Ubuntu can function without a swap partition, no problem about that even if you didn't have one.

But your win7 seems messed up good. Even the windows repair process not discovering it is a sign of that too.

If you follow the link in my signature and run the boot info script as explained there, and post the results here it might show us more.

I ran bootinfoscript, and it appeared to recognise the windows7 installation, it gets weirder and weirder...
anyway, here are the results:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 100149273.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

/dev/sda lemez: 80.0 GB, 80026361856 bájt
255 fej, 63 szektor, 9729 cilinder, összesen 156301488 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          19,533,822   156,296,384   136,762,563   5 Extended
/dev/sda5          48,939,008   100,147,199    51,208,192   7 NTFS / exFAT / HPFS
/dev/sda6         100,149,273   156,296,384    56,147,112   c W95 FAT32 (LBA)
/dev/sda7          19,533,824    25,489,407     5,955,584  82 Linux swap / Solaris
/dev/sda8          25,491,456    48,932,863    23,441,408  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        420c7bae-e3ae-4690-b740-018b3e44db4f   ext4       
/dev/sda5        26F0C9CBF0C9A203                       ntfs       
/dev/sda6        AE3B-5426                              vfat       cuccok
/dev/sda7        05f8137a-c45b-4d92-8c42-111fd461a192   swap       
/dev/sda8        da282e68-0bdf-4158-b543-3ed2251bbd1b   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /home                    ext4       (rw)
/dev/sr1         /media/Disc              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
```

---

### Post by oldfred on 2011-12-01
Please use code tags to make it easier to read long scripts. You highlight what you want in the tags and click on the # in the edit panel above. Or click on tags and paste in between them.

You have Windows in sda5 which is a logical partition. Windows only boots from a primary partition. You probably had a primary partition with the Windows 7 boot files in it before and deleted it.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Your sda5 is also in the middle of the extended partition so it is very difficult to convert back to a primary. It may be best to just create a 100MB boot partition for Windows formated NTFS with the boot flag and use Windows to install/repair that partition to be the boot partition. You should be able to shrink the extended and put sda3 at the end of the drive.

---

### Post by darkod on 2011-12-01
Earlier you said all three bott files I asked about are there. They aren't. Look at sda5, only windows/system32/winload.exe is there.

bootmgr and boot/bcd were probably on another, primary partition that got deleted. That's why it's not detected.
Further more I guess the automatic windows repair process is not working because win7 is on logical partition. Windows doesn't really like that although it can work like this if the boot files were on a primary partition.

---

