---
title: "Can't do a live boot from CD"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by Xynche on 2010-12-23
Two days ago Ubuntu crashed and I had to reformat my computer (I don't know what happened and I couldn't fix it). I'm running Window XP right now and am having trouble booting/installing several distros of linux.

I've tried Kubuntu, Ubuntu, Xbuntu, Puppylinux, and Fedora live CDs and continue to get the same thing.

When I boot, after the bios, I get a flashing "_". I don't get a boot and have to reboot and remove the CD.

I would like to get Xbuntu running as soon as possible. Any help would be great.

EDIT: Also, In windows, when I go to my computer I cannot see the Live CDs. I don't know if this is related in some way.

---

### Post by wilee-nilee on 2010-12-23
Find the key prompt hit at power on that gets you to a boot from menu outside the bios, my key prompt is f12.

This is a per-session boot from your choice, better then changing the bios order and more reliable it seems.

---

### Post by Xynche on 2010-12-23
The only 2 options I have before boot is f1 which is my bios, and f10 which is recovery mode (I'm not sure what that is).

I don't get anything saying "Press f# to boot from CD" if that's what your saying.

---

### Post by wilee-nilee on 2010-12-23
> **Xynche said:**
> The only 2 options I have before boot is f1 which is my bios, and f10 which is recovery mode (I'm not sure what that is).

I don't get anything saying "Press f# to boot from CD" if that's what your saying.

Look on google with per-session boot and your computer model or tell me what it is and I will look.

---

### Post by Xynche on 2010-12-23
Ok, I found out what you meant. When I press Esc I get a list of 
1.Floppy 
2.CD
3.Harddrive

I choose CD and I get the same flashing _

EDIT: Found numerous other problems.

Windows will not boot if there is a CD in the drive or if my external harddrive is plugged in. This situation is getting annoying.

---

### Post by Xynche on 2010-12-23
Bump, Help is still very much needed.

---

### Post by garvinrick4 on 2010-12-23
> **Xynche said:**
> Ok, I found out what you meant. When I press Esc I get a list of 
1.Floppy 
2.CD
3.Harddrive

I choose CD and I get the same flashing _

EDIT: Found numerous other problems.

Windows will not boot if there is a CD in the drive or if my external harddrive is plugged in. This situation is getting annoying. If external USB drive is trying to boot before the HDD then you have USB set to boot that way. 
I would look around in your BIOS or google it until you find instructions. 
There is no doubt it is hitting the USB device first.

---

### Post by Xynche on 2010-12-23
Well, I've just been unplugging it before booting.

In the bios there are four items

CD
Hard drive
Floppy
Networking

I have floppy and network disabled and the hard drive is set to the internal one, not the external.

---

### Post by wilee-nilee on 2010-12-24
Are you able to boot anything with the esc key prompt, with everything not needed unplugged...usb..etc?

Does the computer boot from a thumb and do you have one?

Did you burn the cd's as images?

---

### Post by Xynche on 2010-12-24
> **wilee-nilee said:**
> Are you able to boot anything with the esc key prompt, with everything not needed unplugged...usb..etc?
I can boot windows if I choose Hard drive.

> **wilee-nilee said:**
> Does the computer boot from a thumb and do you have one?
I have one and I'll reboot to see if it shows up under anything in bios.

> **wilee-nilee said:**
> Did you burn the cd's as images?
Yes.

Ok, I checked and under Hard drive I can select USB flash memory. I'll try to make a bootable USB with UNetBootin and post results once it's finished.

---

### Post by Xynche on 2010-12-24
Well, It starts up and gets to the UNetBootin menu. Unfortunatly, when I choose any option (Try Xbuntu, Install Xbuntu) I get a flashing _ like before.

For some reason, I can't boot the pc with Windows XP anymore. Should I reformat and install Windows before I keep going, of just continue troubleshooting until I get it working?

---

### Post by garvinrick4 on 2010-12-24
Run bootscript in wilee-nilees signature and post some one will get grub installed in mbr for you, not a major operation.
#Sorry just noticed you cannot get to a linux desktop:

---

### Post by Xynche on 2010-12-25
Well I got Puppylinux installed but it seems to have a few problems. 

At least I'm running a linux desktop.

I'll try running the bootscript.

---

### Post by Xynche on 2010-12-25
The sdb1 drive is my flashdrive. Also, Puppylinux has a GRUB installer on it, should I run that? (I'm not even sure what GRUB is)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   117,226,304   117,226,242  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011087872 bytes
32 heads, 63 sectors/track, 7761 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,646,175    15,646,113   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7c611981-2296-4e12-b551-a5fd19ef014d   ext3                                     
/dev/sdb1        108E-D5AE                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=2cbafdcd)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/sr0         /mnt/sr0                 iso9660    (ro,relatime,iocharset=utf8)
/dev/sdb1        /mnt/sdb1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)

=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 
```

---

### Post by garvinrick4 on 2010-12-25
Your sda drive (one in machine) shows to be formatted in ext3 which is a linux
format but has no Operating sysyem or boot files installed at all. And in the mbr
(master boot record) shows that your internal drive has a Windows boot manager
installed. So I would say install a operating system in your machine and you always
put grub in sda not sda1 or sda2 but sda.  And grub means your type of boot loader,
linux has a few different typees, Windows has there own. Just a piece of software that
makes the machine boot into the operating system. 
 Ubuntu you format in ext4 and Windows is NTFS choose one and put the disk in your
machine and boot it up and follow directions. Any questions get back on forum and ask
for a little more help.

---

### Post by Xynche on 2010-12-26
What if I can't put grub on "/dev/sda"? It says that it's not linux and wont let me. However it's fine with putting it on "/dev/sda1".

---

### Post by Xynche on 2010-12-26
Ok, so I got grub on there finally. I'm able to boot Puppylinux from my harddrive now. I don't see how any of this makes it so I can boot Xubuntu from the cd though...

Next step?

---

### Post by garvinrick4 on 2010-12-26
As long as you have CD choosen before HDD in Bios CD will boot as long as it is a good
CD. A live  Cd or USB has nothing to do with Hard Drive you are working off of CD when you Boot off of it (put in tray and restart computer).
 What do you want to do with your computer?

---

### Post by Xynche on 2010-12-28
I would like to get Xubuntu installed on my hard drive. When I boot from the cd I get to the menu (Where it asks if I want to try Xubuntu, Install, etc...), I choose try (or install) and I get a flashing _ like described in the first post. 

The only cd I can get to boot it PuppyLinux.

---

### Post by Xynche on 2011-01-04
Bump, I still need help. Any help would be great.

---

