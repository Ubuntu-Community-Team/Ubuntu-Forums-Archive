---
title: "Grub xputs"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2010-10-10
I just upgraded to 10.10 and when my pc restarted, I get a message saying "error:the symbol' grub_xputs' not found" underneath that it says"grub rescue". What do I do next?

---

### Post by drs305 on 2010-10-10
There was a bug in upgrades from Karmic to Lucid that generated the same error message. The solution was to boot to the LiveCD Desktop and reinstall grub-pc.

I wrote a guide last week to detail how to purge and reinstall grub. You could follow the entire procedure or just try to reinstall (install --reinstall) without purging first. I like the 'purging' method as it will replace files the user may have accidentally deleted.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by TimEnid on 2010-10-10
When I boot from the cd, I still get the same screen. I'm unable to load the cd. I chose boot from cd in the bios, but it won't

---

### Post by drs305 on 2010-10-10
Can you test the CD in another computer or test another CD in the same computer? 

I assume you just used it recently for the installation but it sounds like the system isn't using the CD and is proceeding to use the hard drive.

I don't know what error message would be generated, but if you have both 64 and 32 bit install CDs make sure you are using the correct one (at least on the 32-bit machine).

ADDED:  Seems there is also an xputs bug in the 10.04 to 10.10 process. See here:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/609280]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/609280")

---

### Post by TimEnid on 2010-10-10
I didn't used a cd to upgrade. I used the update manager.

---

### Post by drs305 on 2010-10-10
> **TimEnid said:**
> I didn't used a cd to upgrade. I used the update manager.

I found a bug report on updates to 10.10 and added it to my previous post. ^^

---

### Post by TimEnid on 2010-10-10
I read all the comments in the link but am unsure of what I should do next.

---

### Post by TimEnid on 2010-10-10
should I remove the internal drives from my pc?

---

### Post by TimEnid on 2010-10-10
Thanks a lot. This solved my problem. I am now up and running. I owe you.> **drs305 said:**
> There was a bug in upgrades from Karmic to Lucid that generated the same error message. The solution was to boot to the LiveCD Desktop and reinstall grub-pc.

I wrote a guide last week to detail how to purge and reinstall grub. You could follow the entire procedure or just try to reinstall (install --reinstall) without purging first. I like the 'purging' method as it will replace files the user may have accidentally deleted.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by dez93_2000 on 2010-11-11
> **TimEnid said:**
> Thanks a lot. This solved my problem

...but not mine, sadly. Changing boot priority to cd still hits the xputs error then grub rescue. Maybe it's not loading the cd but i don't know what else i can do to make it do so. Tried both LiveCd flavours.

Tried to type my way out of the hole using help here: [http://grub.enbug.org/Manual#GrubShell](http://grub.enbug.org/Manual#GrubShell) but 'help' command isn't recognised.

Did the first 2 bits of this: [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9975071&postcount=5](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9975071&postcount=5) but insmod didn't recognise linux as a thing.

Since i need to reinstall grub ([http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979766&postcount=7](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9979766&postcount=7)) does anyone know 
1. if there are a set of 'grub rescue' commands that actually work to help me reinstall grub either directly, or
2. what i can do to get my cdrom drive booting so i can do this all through the well documented GUI process?

Many thanks in advance. I literally can't believe this hasn't been fixed since last time. No matter how much better the new builds are, they are forever tainted by having to take a full day getting them to work.
drs305 - cheers from the whole community for your posts about this in various fora.

---

### Post by drs305 on 2010-11-11
> **dez93_2000 said:**
> ...but not mine, sadly. Changing boot priority to cd still hits the xputs error then grub rescue. Maybe it's not loading the cd but i don't know what else i can do to make it do so. Tried both LiveCd flavours.


The main way that you could be getting the grub xputs message with a CD inserted and listed first in BIOS is if the CD boot is failing and the BIOS goes to the backup selection (hard drive).

Can you boot other CDs from your computer?

You might also try creating a bootable USB drive or flashdrive. The option is presented on the Ubuntu download page.
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

I'd like to be able to talk you or instruct you through a grub terminal boot, but the xputs error normally means that it isn't completely installed. In most circumstances, the user trying to boot with this error sooner or later runs into a missing or corrupted file that will cause the boot to fail.

---

### Post by dez93_2000 on 2010-11-12
cheers for the ideas. tried the usb method using a 1gb stick (recommends 2) but not recognised in any of my ports. next priority was cdrom which says "booting from cd/dvd" then hits the xputs problem with both 32 & 64bit. Windows boots cds give me a few dots of loading/spinning up then the same.

SO. Any ideas on how to get the usb stick recognised* or the boot cd working or..anything else?

*since i used a 1gb stick instead of the recommended 2, could this be the problem? Reason i ask is that the process worked fine and obviously the iso FITS on a 1gb stick, since it fits on a 700mb cd.

thanks in advance - again!

---

### Post by Quackers on 2010-11-12
Is there an option in your bios to boot from usb stick? If there is it would need to be selected as first or second boot device (ie before or after CD drive but before HDD).

---

### Post by dez93_2000 on 2010-11-12
indeed there is sir, and its selected, followed by cdrom, followed by hard drive.

usb-fdd is the one, right? (i think it's called FDD)

---

### Post by Quackers on 2010-11-12
I'm unsure. Could FDD be for a floppy drive?

---

### Post by sikander3786 on 2010-11-12
> usb-fdd is the one, right? (i think it's called FDD)

I don't think it would be usb-fdd. Sometime on some hardware, flash drives just pop in the Hard Disk Drive menu and you need to set 1st boot device to HDD and then change the boot order of the HDDs themselves and bring your USB drive to the top of the list.

Can you please list your motherboard's make and model?

---

### Post by dez93_2000 on 2010-11-14
Guys, thanks a million for this. My denseness in not guessing FDD meant floppy drive was the problem i guess. Cheers!

---

### Post by bradbury on 2010-11-14
Grub 2 seems to have a problem mixing up the A and B drives.  There is a way to solve it by editing the grub.cfg file I think but I don't know what it is.

My solution: Unplug the power to the non-Ubuntu drive (so there is only a single "A" drive" on the machine, i.e. the one you want to boot Ubuntu off of) [1].  The boot Ubuntu and fix grub.cfg or downgrade back to grub 1.x.

If your system is a real "mixed drive" system, e.g. root on Drive A and user on Drive B then this may be problematic and you'll have to figure out the grub.cfg fix first.

1.  Note, if the install put "Grub 2" into the MBR of Drive B then you are going to have to reinstall grub (presumably boot some LiveCD and get it to re-install grub) to get it into the MBR of Drive A.

---

### Post by bradbury on 2010-11-14
> **TimEnid said:**
> I get a message saying "error:the symbol' grub_xputs' not found" underneath that it says"grub rescue". What do I do next?

This error comes when Grub is looking for additional sub-components on the wrong partition or in my case on the wrong drive.  One can tell this because "grub rescue" does not behave as documented (it is useless as far as I can tell).

You have to get grub to be dealing with the right partitions on the right drive (easiest way -- unplug all drives but the one being used to install Grub & Ubuntu, reinstall, boot from that drive and verify operations).

Not pretty but it seemed to work for me.

---

### Post by Urhixidur on 2010-11-16
I ran into the same problem after upgrading from Ubuntu 10.04 (Lucid) to Ubuntu 10.10 (Maverick).  I can boot from the LiveCD and then, after a little twiddling (installing lvm2, modprobe dm-mod, partprobe), remount my target drives, but grub steadfastly refuses to see the mounted partitions when the time comes to create grub.cfg.  The physical/logical drive/partition configuration did NOT change between before and after the upgrade: it used to boot just fine.

Single physical hard drive (/dev/sda), with three physical partitions:
/dev/sda1 : FAT16, "DellUtility"
/dev/sda2 : ext4, "boot" bootable, mounted as /boot
/dev/sda3 : LVM, "lvm_vol_grp"

The logical LVM partitions are:
/dev/lvm_vol_grp/root : ext4, "root", mounted as /
/dev/lvm_vol_grp/home : ext4, "home", mounted as /home
/dev/lvm_vol_grp/share : ext4, "share", mounted as /share
/dev/lvm_vol_grp/swap : swap, "swap", not mounted

Once running from LiveCD, I mkdir /target and mount the four target partitions there (/target, /target/boot, /target/home, /target/share).  I then try "grub-install --root-directory=/target /dev/sda", which produces no error but does not create /target/boot/grub/grub.cfg

If I try to update-grub I get "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)"  I get the same message if I chroot to /target and then try to update-grub.

Here is what the bootinfoscript reports from the LiveCD, and later from chroot /target:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 152888 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

lvm_vol_grp-root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

lvm_vol_grp-home: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

lvm_vol_grp-share: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

lvm_vol_grp-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        128,520       610,469       481,950  83 Linux
/dev/sda3             610,470 1,953,525,167 1,952,914,698  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/lvm_vol_grp-home 2e4be6e0-0ac6-4505-828d-71774caf84c5   ext4                                     
/dev/mapper/lvm_vol_grp-root 331525a6-2db5-48c4-832d-b6d4beb7db92   ext4                                     
/dev/mapper/lvm_vol_grp-share e31fa943-d4e2-41ad-96ab-47ff7968fc00   ext4                                     
/dev/mapper/lvm_vol_grp-swap f856452e-3dd0-48a8-b6f6-5070d562c889   swap                                     
/dev/sda1        07D8-061B                              vfat       DellUtility                   
/dev/sda2        6b70b7ff-381b-4a15-a12c-bc9a53981125   ext4       boot                          
/dev/sda3        f7KkI3-kg0x-pFVS-P9RT-HSLE-JJ4M-NJqmLV LVM2_member                               
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
lvm_vol_grp-home
lvm_vol_grp-root
lvm_vol_grp-share
lvm_vol_grp-swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/lvm_vol_grp-root /target                  ext4       (rw)
/dev/mapper/lvm_vol_grp-home /target/home             ext4       (rw)
/dev/mapper/lvm_vol_grp-share /target/share            ext4       (rw)
/dev/sda2        /target/boot             ext4       (rw)


========================= lvm_vol_grp-root/etc/fstab: =========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/lvm_vol_grp-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=6b70b7ff-381b-4a15-a12c-bc9a53981125 /boot           ext4    defaults        0       2
/dev/mapper/lvm_vol_grp-home /home           ext4    defaults        0       2
/dev/mapper/lvm_vol_grp-share /share          ext4    defaults        0       2
/dev/mapper/lvm_vol_grp-swap none            swap    sw              0       0

============= lvm_vol_grp-root: Location of files loaded by Grub: =============


    .1GB: initrd.img
    .1GB: initrd.img.old
    .1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```Note the message "Grub 2 is installed in the boot sector of sda2 and looks at sector 152888 of the same hard drive for core.img, but core.img can not be found at this location"  The exasperating thing is that there is a /target/boot/grub/core.img file...

For comparison, here is the bootinfoscript result from chroot /target :
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         


============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/lvm_vol_grp-root /                        ext4       (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
/dev/sda2        /boot                    ext4       (rw,relatime,barrier=1,data=ordered)
/dev/mapper/lvm_vol_grp-home /home                    ext4       (rw,relatime,barrier=1,data=ordered)
/dev/mapper/lvm_vol_grp-share /share                   ext4       (rw,relatime,barrier=1,data=ordered)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)

=============================== StdErr Messages: ===============================

  /proc/mounts: _get_sysfs_dir: fopen %s failed: No such file or directory
  /proc/devices: fopen failed: No such file or directory
  Failed to create lvm type filter
  Internal error: _vginfos list should be empty
  You have a memory leak (not released memory pool):
   [0x2480780]
  You have a memory leak (not released memory pool):
   [0x2480780]
sort: open failed: /tmp/BootInfo0/BLKID: No such file or directory

```Help??

---

### Post by drs305 on 2010-11-16
Urhixidur,

I don't use lvm but I believe your problem is that you aren't also mounting the /boot partition. 

For installing grub on a more conventional setup, if you had Ubuntu on sda1 and a separate /boot partition on sda2 you would do it this way:

*Example for demonstration purposes only:*
```
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda2 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Use this principle and apply it to installing your lvm setup.

---

### Post by steve.dake on 2010-12-07
**Very **easy fix -worked for me and took about 2 minutes:

[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/")

---

### Post by Jean-Noel on 2011-02-08
Tx for having taken the time to write this solution. It solved my problem.

Here is the text I put on LinkedIn "Ubuntu Users ( 10.000+ members ) Official Group" :

What stops XP-users from switching to Ubuntu? Can we make a plan together to help those millions of XP-users (63% market share) not to have to buy a new computer?

[http://www.linkedin.com/groupItem?view=&gid=27258&type=member&item=21625037&qid=954d0dd5-6896-40c2-88f9-a57f5c17c3b2&goback=%2Egde_27258_member_21625037%2Egmp_27258](http://www.linkedin.com/groupItem?view=&gid=27258&type=member&item=21625037&qid=954d0dd5-6896-40c2-88f9-a57f5c17c3b2&goback=%2Egde_27258_member_21625037%2Egmp_27258)

****************************************************

1 good reason about what stops ANY (regular) computer-users from switching to Ubuntu? 

February 7th, 4 months after Ubuntu 10.10 launch, I thought that most of the bugs of ver. 10.10 are now solved and that it could be a good time to migrate my 10.04LTS version to 10.10

I was wrong! 
Following the 10.10 update (launched with update manager), after rebooting my machine, I got a very friendly black screen with the following message:

Error : the symbol ‘grub_xputs’ not found. 
grub rescue>  _ 

No matter about what and how. 
A regular non computer literate user doesn’t care about the good and bad reasons why this happens, he will just be desperate because his machine doesn’t work anymore after an upgrade to the latest version of everything on his machine, simply because a several months old bug isn’t still corrected by a software editor which he trusted…

---

