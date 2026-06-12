---
title: "Fresh install of 12.04 leads to grub prompt after update"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by jenks on 2012-05-03
The situation couldn't be much simpler. Yesterday I downloaded the alternate installer for 12.04 and installed it as the only system on the only hard drive in a system, selecting guided partitioning using the enitre disk. The entire installation went flawlessly, and the network was available the enitre time for package retrieval. The system then rebooted perfectly, and I proceeded to allow the update manager, which launched spontaneously, to download and install all new updates, bringing the entire system up to date as of about an hour ago. After installing openssh-server manually, I rebooted the system as update-manager requested - to find myself stuck at the grub prompt. I was surprised by this given that the previous - and only - boot of this system had been successful.

The screen says:

GNU GRUB version 1.99-21ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

What I have tried so far is to rerun grub-install according to the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708"). Although the 12.04 live CD fails to boot completely, apparently having a problem with the video driver, which is why I used the alternate installer, I was able to reach the command line through Ctrl-Alt-F1. The "sudo fdisk -l" command shows the following partitions:

Disk: /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 63481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical); 512 bytes / 512 bytes
I/O size (minimum/optimal); 512 bytes / 512 bytes
Disk identifier: 0x00019e7e

   Device     Boot    Start         End      Blocks   Id  System
/dev/sda1       *      2048   584509439   292253696   83  Linux
/dev/sda2         584511486   586072063      780289    5  Extended
/dev/sda5         584511488   586072063      780289   82  Linux swap / Solaris

As I said, the commands:

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
sudo grub-install --root-directory=/media/sda1 /dev/sda

completed successfully, but had no effect on the failure to boot.

I assume that when I updated my system that something was wrong with the latest kernel put into the repository and that it needs to be replaced, so I hope that my other 12.04 system will not be affected. Meanwhile, I could use suggections for how to boot and restore my new, bricked system.

---

### Post by oldfred on 2012-05-03
While root should work the new grub 1.99 suggest boot.

sudo mount /dev/sda1 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

Some have had issues with larger / (root) paritions, but that is usually 1GB or more. I often suggest a 25GB / and use the rest as /home or data.

---

### Post by jenks on 2012-05-03
I'll give that a try. Meanwhile I dug up some very old notes of mine and was able to boot from the grub prompt using the following commands:

linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

EDIT: I tried your suggestion, and although grub-install again ran without errors, the system still boots to the grub prompt. Likewise, when I run:

sudo grub-install /dev/sda

from the booted system it also does not correct the boot failure.

---

### Post by p-dh on 2012-05-03
I just installed 12.04 onto a new drive on my PC. I decided to change the partition table and move things around after the installation - including deleting the first partition on the drive. I ended up having to do a complete reinstall of grub - including reinstalling it on the root partition. Here are the steps I took:
> [LIST]
[*]sudo fdisk -l (From that you need to find the device name of your Ubuntu drive, something like “/dev/sd***xy***&#8243; - where ***x*** is the drive and ***y*** is the partition.)
[*]sudo mount /dev/sd***xy*** /mnt
[*]sudo mount --bind /dev /mnt/dev
[*]sudo mount --bind /proc /mnt/proc
[*]sudo mount --bind /sys /mnt/sys
[*]sudo chroot /mnt
[*](optional, only if you're on Ubuntu/Debian and wish to reinstall) apt-get install grub-pc
[*]grub-mkconfig -o /boot/grub/grub.cfg (insure that there are NO error messages)
[*]grub-install /dev/sd***x*** (try grub-install --recheck /dev/sd***xy*** if it fails)
[*]Ctrl+D (to exit out of chroot)
[*]sudo umount /mnt/dev
[*]sudo umount /mnt
[/LIST]

Try it out and see if it works better.

Paul :cool:

---

### Post by oldfred on 2012-05-03
p-dh's method is a full chroot.

But if you can manually boot, you should also try reinstalling grub from your install.

sudo grub-install /dev/sda

or 
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And/or a full reinstall of grub2. You do not have to chroot if you can boot into your install.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If none of those actually work, I would check BIOS for IDE only mode and or shrink / to a much smaller size and make the rest of the drive /home.

---

### Post by jenks on 2012-05-03
The "sudo dpkg-reconfigure grub-pc" command worked, keeping all the default values.

Thank you!

---

### Post by mysteryDave on 2012-12-01
> **jenks said:**
> I'll give that a try. Meanwhile I dug up some very old notes of mine and was able to boot from the grub prompt using the following commands:

linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

EDIT: I tried your suggestion, and although grub-install again ran without errors, the system still boots to the grub prompt. Likewise, when I run:

sudo grub-install /dev/sda

from the booted system it also does not correct the boot failure.

I am having this exact problem.

I install 12.04 and it runs great, until I run updates and then the next boot will go to the grub command line.
I have reinstalled from scratch several times and run updates a few at a time to try and identify the culprit, which appears to be the kernel update.

I'd like to find a better solution than re installing from scratch each time, to preserve installed software and data and so am following your steps.

My sudo fdisk -l output is more confused as I am running nvidia fake raid. ( I have 4 disks split into 2x2 mirrors, one running windows, and the otherrunning Ubuntu):

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd602d602

** Device Boot***** Start******** End***** Blocks** Id* System
/dev/sda1** ********** 63** 781401599** 390700768+** 7* HPFS/NTFS/exFAT

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050ea7

** Device Boot***** Start******** End***** Blocks** Id* System
/dev/sdb1*********** 2048** 775135231** 387566592** 83* Linux
/dev/sdb2****** 775137278** 781422591**** 3142657*** 5* Extended
/dev/sdb5****** 775137280** 781422591**** 3142656** 82* Linux swap / Solaris

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd602d602

** Device Boot***** Start******** End***** Blocks** Id* System
/dev/sdc1** ********** 63** 781401599** 390700768+** 7* HPFS/NTFS/exFAT

Disk /dev/mapper/nvidia_caadbijb: 400.1 GB, 400088456192 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422766 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd602d602

********************* Device Boot***** Start******** End***** Blocks** Id* System
/dev/mapper/nvidia_caadbijb1** ********** 63** 781401599** 390700768+** 7* HPFS/NTFS/exFAT

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050ea7

** Device Boot***** Start******** End***** Blocks** Id* System
/dev/sde1*********** 2048** 775135231** 387566592** 83* Linux
/dev/sde2****** 775137278** 781422591**** 3142657*** 5* Extended
/dev/sde5****** 775137280** 781422591**** 3142656** 82* Linux swap / Solaris

Disk /dev/mapper/nvidia_caadbijb1: 400.1 GB, 400077586944 bytes
255 heads, 63 sectors/track, 48639 cylinders, total 781401537 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

*********************** Device Boot***** Start******** End***** Blocks** Id* System
/dev/mapper/nvidia_caadbijb1p1** ?** 218129509* 1920119918** 850995205** 72* Unknown
/dev/mapper/nvidia_caadbijb1p2** ?** 729050177* 1273024900** 271987362** 74* Unknown
/dev/mapper/nvidia_caadbijb1p3** ?** 168653938** 168653938********** 0** 65* Novell Netware 386
/dev/mapper/nvidia_caadbijb1p4***** 2692939776* 2692991410****** 25817+** 0* Empty

Partition table entries are not in disk order

Disk /dev/mapper/nvidia_aagbfhjd: 400.1 GB, 400088456192 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422766 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050ea7

********************* Device Boot***** Start******** End***** Blocks** Id* System
/dev/mapper/nvidia_aagbfhjd1*********** 2048** 775135231** 387566592** 83* Linux
/dev/mapper/nvidia_aagbfhjd2****** 775137278** 781422591**** 3142657*** 5* Extended
/dev/mapper/nvidia_aagbfhjd5****** 775137280** 781422591**** 3142656** 82* Linux swap / Solaris

Disk /dev/mapper/nvidia_aagbfhjd1: 396.9 GB, 396868190208 bytes
255 heads, 63 sectors/track, 48249 cylinders, total 775133184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_aagbfhjd1 doesn't contain a valid partition table

Disk /dev/mapper/nvidia_aagbfhjd2: 3218 MB, 3218080768 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6285314 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

*********************** Device Boot***** Start******** End***** Blocks** Id* System
/dev/mapper/nvidia_aagbfhjd2p1************** 2**** 6285313**** 3142656** 82* Linux swap / Solaris

Disk /dev/mapper/nvidia_aagbfhjd5: 3218 MB, 3218079744 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6285312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_aagbfhjd5 doesn't contain a valid partition table


I have tried to boot from the grub menu using:
linux /vmlinuz /dev/mapper/nvidia_aagbfhjd1
and
linux /vmlinuz /devsdb1
but get this error:
error: not a regular file.

If I try the next commands I get errors that I need to load the kernel first, and that there is no loaded kernel. Any ideas?

---

### Post by mysteryDave on 2012-12-01
Ok. I managed to start using an Ubuntu CD and was the noble to follow the first 6 steps suggested by p-dh:

> **p-dh]
sudo fdisk -l (From that you need to find the device name of your Ubuntu drive, something like “/dev/sdxy&#8243 said:**
> 

Then reconfigured grub as suggested by oldfred:

[QUOTE=oldfred;11902505]
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


Next boot showed the familiar looking menu:
Ubuntu with Linux 3.2.0-34-generic
Ubuntu with Linux 3.2.0-34-generic (recovery mode)
Previous Linux versions

Selecting the first gives this error:
error: invalid magic number.
error: you need to load the kernel first.

Selecting the second gives this error:
Loading Linux 3.2.0-34-generic ...
error: file not found.
Loading initial ram disk ....
error: you need to load the kernel first.

Selecting the third gives a new menu:
Ubuntu with Linux 3.2.0-29-generic
Ubuntu with Linux 3.2.0-29-generic (recovery mode

Either of these boots fine so it looks like the upgrade to -34 doesn't work.. Anyone seen this before?

---

