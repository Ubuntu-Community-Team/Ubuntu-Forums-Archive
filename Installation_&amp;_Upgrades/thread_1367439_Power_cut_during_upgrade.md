---
title: "Power cut during upgrade"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Celestianpower on 2009-12-29
Hello,

My parents were updating our Ubuntu 9.04 to 9.10, and it seemed to be going fine, but halfway through the upgrade, there was a power cut. When we got power back, Ubuntu wouldn't load at all. When we try to boot, the screen says:

> Booting 'Ubuntu 9.10, kernel 2.6.31-15-386

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vwmlinux-2.6.31-15-386 root=/dev/mapper/Ubuntu-root ro quiet splash

Error 15: File not found

Press any key to continue...

When we do press any key, we get GRUB, but all of the options lead back to the screen as above. Does anyone have any ideas of how to fix this?

We have bought a new Ubuntu CD and are happy to reinstall Ubuntu fresh, but there are lots of files on the hardrive at the moment that we need and want to keep, so if we have to do this, is there any way of recovering them?

Thanks in advance!
Celestianpower.

---

### Post by Jenkins1 on 2009-12-29
If you insert the cd and select your language and then select "try ubuntu without any change to your computer [https://help.ubuntu.com/community/LiveCD#Using%20your%20LiveCD]("https://help.ubuntu.com/community/LiveCD#Using%20your%20LiveCD") Have a look at these two pictures to see what I am on about. Using the live cd option boots the computer and runs it from the ram and cd, therefore not affecting your hard dirve. You will reach a normal desktop like you are use to. You can use this to open your ubuntu hard disk from the "places" menu. Any user data is located in the "home" folder. copy any thing you want across to a a flash drive. Your user data shouldn't be affected by the upgrade.

---

### Post by Celestianpower on 2009-12-29
Ok, I have done this, but the home folder is empty - it has empty folders of Documents, Downloads, etc :S. Could the files be on a different part of the hardrive that Ubuntu hasn't automatically mounted?

---

### Post by Jenkins1 on 2009-12-29
Have you looked in the home folder on your computer hard disk or the live cd home folder? You need to select one of the hard disks below the "computer" icon in the "places" menu. You then need to navigate to the home directory on that disk.

---

### Post by Celestianpower on 2009-12-29
There are no hard disks underneath the "computer" icon, just "Floppy Drive".

---

### Post by Jenkins1 on 2009-12-29
Try clicking on the "computer" icon and seeing if there are any extra hard disks listed. Also please go Aplications > Accessories > Terminal and type ```
sudo fdisk -l
```
Please copy and paste the out put here. It will give us an idea of your hard drive layout.

---

### Post by Celestianpower on 2009-12-29
On clicking "computer", I get just "Floppy Drive" and "Filesystem".

The output of 'sudo lshw -C disk' is:
> ubuntu@ubuntu:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: Maxtor 6E040L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: NAR6
       serial: E11MMVGN
       size: 38GiB (41GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6f6b2d4d
  *-cdrom
       description: CD-R/CD-RW writer
       product: CD-RW SOHR-5238S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 4S06
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted


---

### Post by Jenkins1 on 2009-12-29
Sorry my fault I said the wrong command please post the output of ```
sudo fdisk -l
```
Have you used irc? It would make it a bit easier go to [http://shotofjaq.org/chat/]("http://shotofjaq.org/chat/") and change #shotofjaq to #ubuntu-uk and type in a nickname. I am ubuntujenkins on the channel. information about irc can be found here[https://wiki.ubuntu.com/InternetRelayChat]("https://wiki.ubuntu.com/InternetRelayChat") it just means that we can communicate quicker.

---

### Post by Jenkins1 on 2009-12-29
sorry I could not help. I will be interested in how it is solved.

---

### Post by Celestianpower on 2009-12-29
The output of 'sudo fdisk -l' is: 
> ubuntu@ubuntu:~$ sudo fdisk -l
       
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f6b2d4d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        4998    39897427+   5  Extended
/dev/sda5              32        4998    39897396   8e  Linux LVM


My GParted window is attatched.

Can anyone else help?

---

### Post by Jenkins1 on 2009-12-30
bump!

---

### Post by ajgreeny on 2010-01-01
I note the main ubuntu partition is on an LVM partition so will make life more difficult.  In fact in a multiboot system it can be a real pain if you are not au-fait with dealing with those things, and mounting can be a problem.

You will need to ensure that you have the lvm packages installed on the live CD, which I am not sure are there by default, so install them if needed, and then investigate how you can actually mount an lvm partition in a normal ext3 or ext4  install, as I have no clue in detail how to do it.

OK, a quick look got me to this page [http://linux-sxs.org/storage/fedora2ubuntu.html](http://linux-sxs.org/storage/fedora2ubuntu.html)

---

### Post by Celestianpower on 2010-01-07
I haven't been able to get the Internet to run on the live CD version of Ubuntu, so I tried downloading the .deb files onto a pendrive and transfering them accross.

I downloaded [http://packages.ubuntu.com/karmic/lvm2](http://packages.ubuntu.com/karmic/lvm2), and it came up with:

```
Error: Dependency is not satifiable: libdevmapper1.02 (>= 2:1.02.02-2)
```

so I downloaded [http://packages.ubuntu.com/karmic/libdevmapper1.02.1](http://packages.ubuntu.com/karmic/libdevmapper1.02.1), which the website tells me is the dependency of lvm2, and it said the same version is already installed. I reinstalled it anyway, and still get the same response when trying to install lvm2.

Does anyone have any ideas?

---

