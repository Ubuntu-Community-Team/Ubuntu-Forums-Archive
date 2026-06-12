---
title: "USB drives don't recognize hardware plugged into them."
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by vanagonman on 2008-11-16
After upgrading to 8.10 my usb drives do not recognize any external hardware connected to them. I've tried both my flash drive, external dvd player, and printer and nothing works like it had before with version 8.04. I hope this info helps.

zach@zach-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e940e94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24133   193848291   83  Linux
/dev/sda2           24134       24321     1510110    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
zach@zach-desktop:~$ sudo blkid
/dev/sda1: UUID="7c49a3f1-6f03-4dba-97d3-4b6067761d69" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="06d410d5-ffdd-4c57-be78-e5d45cb15935" 
zach@zach-desktop:~$ sudo lshw -C disk
PCI (sysfs)  
  *-disk                  
       description: ATA Disk
       product: ST3200822A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.01
       serial: 4LJ0T7A8
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0e940e94
  *-cdrom
       description: CD-R/CD-RW writer
       product: LTR-52327S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: QS58
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc

Thanks in advance!!!

---

### Post by PhilCash on 2008-11-17
G'day,
Did you ever get your USB ports working?

cheers,
Phil

---

### Post by vanagonman on 2008-11-18
no i'm still having the same issues. do you have any ideas what the problem is?

---

### Post by PhilCash on 2008-11-18
G'day vanagonman,

No luck yet, but my previous experiences with Ubuntu makes me confident of a fix soon if we keep digging and prompting. I've submitted a bug and it is already being investigated. Its at
[https://bugs.launchpad.net/ubuntu/+bug/299020](https://bugs.launchpad.net/ubuntu/+bug/299020)
If you find anything, please let me know.
Good luck,
Phil

---

### Post by PhilCash on 2008-11-24
G'day vanagonman,

I've had success with the first tip in the following page:

[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
and using the instructions in:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I still don't know the cause, or if this needs to be put in the GRUB line as a permanent fixture. Keep an eye on [https://bugs.launchpad.net/ubuntu/+bug/299020](https://bugs.launchpad.net/ubuntu/+bug/299020) for further revelations if this is of any help...

Cheers,
Phil

---

### Post by vanagonman on 2008-11-25
hi philcash,

good to hear that you were successful with this problem. :)

what is the command you need to type to get to the /boot/grub/menu.lst for setting the kernel parameters?

If I enter that in the command line it returns "command not found."

Thanks,
vanagonman

---

