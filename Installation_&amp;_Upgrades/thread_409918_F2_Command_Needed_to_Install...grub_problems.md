---
title: "F2 Command Needed to Install...grub problems?"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by sunksullen on 2007-04-15
Tried to install 2nd hard-drive.   I installed ubuntu to both hardrives but believe that the 2nd hard-drive is non-functional... we have disconnected it.  Now when we boot up with second hard-drive disconnected we get a blinking cursor. I'm pretty sure that GRUB is trying to boot to second harddrive..(the second harddrive was slave...the primary drive is master) 

When we press the F2 key...it takes about 4 minutes but boots into ubuntu.  I type the command:         sudo lshw -C disk             and get:



 *-disk                  
       description: ATA Disk
       product: ST340016A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 3.19
       serial: 3HSCDLQQ
       size: 37GB
       capacity: 37GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 35GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 1466MB
          capabilities: extended partitioned partitioned:extended



----------------
Our configuration for menu.lst in /boot/grub is:

-----
title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet
boot


-------------


  Seems like it is trying to boot to the second old hard-drive that doesn't exist. ??   Could you please tell me the correct settings??? I've been messing with it all night and can't seem to get the correct configuration.


Please help!!!!!!!!!!!!

---

### Post by zvacet on 2007-04-15
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")

---

### Post by sunksullen on 2007-04-15
I went to that link and followed the instructions...rebooted my computer and NO success.  Went back to the link and tried the instructions below...still no luck...spent time on the chatrooms..and was given a command I lost which gave detailed information about my current harddrive setup.  Was then told to reinstall ubuntu...did this... NO luck...I noticed during the installation setup that there was an option to change my harddrive settings for grub..I don't know what to put for the configuration...any ideas??? Thanks!

---

### Post by bulldog on 2007-04-15
Connect both hdd's and boot into ubuntu or use the live cd.
Type in a terminal```
sudo fdisk -l
``` to see if both hdd's are recognized,and how they are partitioned.

You can also take a look in /etc/fstab if there's something referring to the second hdd.

As I can see for now,you're menu.lst is correct,but I need more info to be absolutely sure :D

---

