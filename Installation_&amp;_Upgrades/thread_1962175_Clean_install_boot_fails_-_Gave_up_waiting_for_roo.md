---
title: "Clean install boot fails - Gave up waiting for root device"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by strask on 2012-04-20
After some troubles figuring out how to install correctly onto my raid volume, I was able to use the alternate install cd (12.04 beta 2) to get what seemed like an error-free install.

Grub comes up fine and is able to boot into windows 7.

Booting ubuntu normally hangs at a purple screen. Booting in recovery mode makes some progress before failing like this:```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0c65a8c2-a7654613-aa98-16ff0119ceb9 does not exist.
Dropping to a shell!
```
And leaves me at a (initramfs) prompt.

The boot command line is as expected, same as in grub. root= the uuid that the error message says is missing.

ls /dev/disk shows that there is no by-uuid directory at all. Only by-id and by-path.

ls /dev/mapper shows my boot volume, however, so I tried rebooting with a modified boot commandline, using the device name (/dev/mapper/isw_bhiiebfiid_Volume0) instead of the uuid.

It gets about the same amount through the boot process before giving me this:```

mount: mounting /dev/mapper/isw_bhiiebfiid_Volume0 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.
```
...and I'm back to the initramfs shell.

I ran the bootinfoscript in case that helps, here is the output:```
Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/mapper/isw_bhiiebfiid_Volume0...
Searching sda1 for information...
Searching sda2 for information...
Searching sda3 for information...
Searching sda4 for information...
Searching isw_bhiiebfiid_Volume01 for information...
Searching isw_bhiiebfiid_Volume02 for information...
Searching isw_bhiiebfiid_Volume03 for information...
Searching isw_bhiiebfiid_Volume04 for information...
Searching isw_bhiiebfiid_Volume05 for information...
Searching isw_bhiiebfiid_Volume06 for information...
Searching isw_bhiiebfiid_Volume07 for information...

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Downloads/".

=======

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of
    /dev/mapper/isw_bhiiebfiid_Volume0 and looks at sector 1 of the same hard
    drive for core.img. core.img is at this location and looks for
    (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:
isw_bhiiebfiid_Volume01: _______________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhiiebfiid_Volume02: _______________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhiiebfiid_Volume03: _______________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhiiebfiid_Volume04: _______________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

isw_bhiiebfiid_Volume05: _______________________________________________________
    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhiiebfiid_Volume06: _______________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bhiiebfiid_Volume07: _______________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    23,070,719    23,068,672  27 Hidden
NTFS (Recovery Environment)
/dev/sda2          23,070,720    23,275,519       204,800  27 Hidden
NTFS (Recovery Environment)
/dev/sda3    *     23,275,520 1,181,417,445 1,158,141,926   7 NTFS /
exFAT / HPFS
/dev/sda4       1,181,417,470 1,953,535,999   772,118,530   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: isw_bhiiebfiid_Volume0
_____________________________________________________________________

Disk /dev/mapper/isw_bhiiebfiid_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bhiiebfiid_Volume01              2,048    23,070,719
 23,068,672  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_bhiiebfiid_Volume02         23,070,720    23,275,519
    204,800  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_bhiiebfiid_Volume03   *     23,275,520 1,181,417,445
1,158,141,926   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhiiebfiid_Volume04      1,181,417,470 1,953,535,999
772,118,530   5 Extended
/dev/mapper/isw_bhiiebfiid_Volume05      1,214,189,568 1,316,589,567
102,400,000  83 Linux
/dev/mapper/isw_bhiiebfiid_Volume06      1,316,591,616 1,953,535,999
636,944,384  83 Linux
/dev/mapper/isw_bhiiebfiid_Volume07      1,181,417,472 1,214,189,567
 32,772,096  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/mapper/isw_bhiiebfiid_Volume0p1 BC8C7ECC8C7E80A6
     ntfs       BIOS_RVY
/dev/mapper/isw_bhiiebfiid_Volume0p2 C45681355681296E
     ntfs       System
/dev/mapper/isw_bhiiebfiid_Volume0p3 3A4C85824C8539A1
     ntfs       OS_Install
/dev/mapper/isw_bhiiebfiid_Volume0p5
0c65a8c2-a765-4613-aa98-16ff0119ceb9   ext4       linuxroot
/dev/mapper/isw_bhiiebfiid_Volume0p6
01ba4dea-ab44-4fe2-b7d3-45ba25a672b9   ext4       linuxhome
/dev/mapper/isw_bhiiebfiid_Volume0p7
171d25da-d5f5-4572-83b2-ea78d73351e5   swap
/dev/sda                                                isw_raid_member
/dev/sdb                                                isw_raid_member
/dev/sr0                                                iso9660
Ubuntu 12.04 LTS amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bhiiebfiid_Volume0
isw_bhiiebfiid_Volume0p1
isw_bhiiebfiid_Volume0p2
isw_bhiiebfiid_Volume0p3
isw_bhiiebfiid_Volume0p4
isw_bhiiebfiid_Volume0p5
isw_bhiiebfiid_Volume0p6
isw_bhiiebfiid_Volume0p7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on isw_bhiiebfiid_Volume01

Unknown BootLoader on isw_bhiiebfiid_Volume02


Unknown BootLoader on isw_bhiiebfiid_Volume03


Unknown BootLoader on isw_bhiiebfiid_Volume04


Unknown BootLoader on isw_bhiiebfiid_Volume05


Unknown BootLoader on isw_bhiiebfiid_Volume06


Unknown BootLoader on isw_bhiiebfiid_Volume07



========= Devices which don't seem to have a corresponding hard drive: =========

sdc

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume01: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume02: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume03: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume03: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume04: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume04: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume05: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume05: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume06: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume06: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume07: No such file or directory
hexdump: /dev/mapper/isw_bhiiebfiid_Volume07: No such file or directory
```

---

### Post by darkod on 2012-04-20
There are some messages that /dev/sda3 and /dev/sda4 are outside the disk, but I'm not sure since the disk is a raid member anyway.

The modification you tried to boot with Volume0, that's the whole raid device. The root partition is Volume0p5, the partition #5 on it. See if it can boot it like that.

---

### Post by strask on 2012-04-20
Hi Darko, thanks for looking at this.

> **darkod said:**
> The modification you tried to boot with Volume0, that's the whole raid device. The root partition is Volume0p5, the partition #5 on it. See if it can boot it like that.

When I do that, it fails the same way it does when it's using the uuid; gave up waiting for root device and "ALERT! /dev/mapper/isw_bhiiebfiid_Volume0p5 does not exist."

I should have been more clear before, when I am at the (initramfs) prompt after it gives up, if I do 'ls /dev/mapper', I see the control entry, and the Volume0 entry, and that's it. There are no devices present for the individual partitions.

---

### Post by strask on 2012-04-21
Anyone have ideas on this?

Since the install CDs can access the partitions on my raid volume, I feel like ubuntu should be able to work once booted. It just feels like the boot process needs to load an extra driver or module to see the individual partitions so that it can mount /.

---

### Post by darkod on 2012-04-21
Can you at least boot the system in the ubuntu recovery mode from the boot menu?

---

### Post by strask on 2012-04-21
No, what we have been discussing IS an attempt to boot in recovery mode.

Like I said though, I can boot the livecd no problem and it recognizes all the hardware, finds the disk, etc.

---

### Post by darkod on 2012-04-21
OK. If live mode can read the partitions, you can chroot into it and try to modify the /etc/default/grub file.

To chroot, you first need to prepare mounting the root partition:
```
sudo mount /dev/mapper/XXXXX_Volume0p5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are inside the installation and can modify the file:
```
gedit /etc/default/grub
```

In the line GRUB_CMDLINE_LINUX="" change it to "rootdelay=30" for example. If that doesn't work, change it again to 60 or 90. To recreate grub.cfg with the new value run:
```
update-grub
```

Also, another option is under that line to add a new line with:
GRUB_DISABLE_LINUX_UUID=true

Once you do all of that and run the update-grub, exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and see if that helped anything.

On another note, there is always the possibility that being a Beta it still has some issues and that is why it's not working. See if the above can help.

---

### Post by strask on 2012-04-21
Thank you for this! I will go try it now. I had attempted doing some stuff of this ilk but ran into troubles because I didn't know the magic to make proc/dev/sys mount under the chrooted environment. :)

---

### Post by darkod on 2012-04-21
Yeah, that group of four commands is standard preparation for chroot. First you mount the root and then bind the proc, dev and sys.
Note that if there is a separate /boot partition that needs to be mounted after root too.

I hope it works.

---

### Post by strask on 2012-04-21
Well, it didn't work but was educational.

Setting the delay up to 90 just made me wait longer for the same failure. 
It didn't seem to matter if I used UUIDs or not.
Oh, and for some odd reason grub forgot about my windows install and would only try to boot the broken linux.

So I got to thinking and figured I would backtrack to 11.10 and see if it was an issue with the beta version of 12.04, like you suggested it might be.

Guess what? I'm typing to you from my perfectly-working 11.10 install. :)

So all that remains is to figure out how to write up a useful bug report on 12.04. 

Thanks for all your help, marking this thread solved.

Edit: This bug was already known, the bug report is at [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/931929](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/931929)

---

### Post by bryanl on 2012-05-04
I am having this problem on an old laptop with a Promise controller.

Worked fine with 11.10 but a new install of 12.04 lost both the drive and the touchpad. (multiple monitors on the laptop also doesn't work, neither does the all-in-one HP fax)

One suggestion I have seen is to add the module name needed to /etc/initramfs-toos/modules and then run update-initramfs - I had problems with that probably because of the dev, proc, and sys binding so will have to give it another shot.

thanks for the bug link. Precise is looking to be quite a regression for me at this point. (but I learn a lot trying to figure these things out!)

---

### Post by strask on 2012-05-05
I used the workarounds from the bug report to get up and running on 12.04; it took a bit of work but now everything works smoothly for me. Hopefully it will be the same for you.

---

### Post by Nizpiz on 2012-05-10
I may be having the same issue as you, but when I attempted to perform the fix by editing /usr/share/initramfs-tools/scripts/local-top/dmraid, I get down to the scripts directory and find no directory within named local-top.
 
Did dmraid move in 12.04?

---

### Post by strask on 2012-05-10
I don't know. It was still there when I resolved the problem on 12.04 beta 2, and I've installed all the updates so I should be running code pretty much identical to 12.04 release. Here is the contents of my scripts directory: ```

root@reptoid:/usr/share/initramfs-tools/scripts# ls
functions    init-premount  local         local-premount  nfs      panic
init-bottom  init-top       local-bottom  local-top       nfs-top
root@reptoid:/usr/share/initramfs-tools/scripts# uname -a
Linux reptoid 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
root@reptoid:/usr/share/initramfs-tools/scripts# 

```

When you fall into the initramfs shell, can you recover by typing```
dmraid -ay
```followed by 'exit'? You might be having more severe problems than what I experienced.

---

### Post by ITfromScratch on 2013-03-29
I was having this same problem, but only on computers with 2 hard drives. If the computer only had 1 hard drive there was no problem. 

I figured out, mostly by luck, that if I installed 10.04 and then did an in place upgrade to 12.04 the problem went away. I don't know why, but it did.

Source: [http://www.itfromscratch.com/ubuntu-boot-error-workaround/](http://www.itfromscratch.com/ubuntu-boot-error-workaround/)

---

### Post by Homechicken on 2013-04-05
I had a similar problem last night when I upgraded to 12.04 LTS. Specifically, it said:
> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/isw_cafgghefcf_Volume01 does not exist. Dropping to a shell!

The /dev/mapper directory had new device names for the old system partitions (Volume01 changed to Volume0p1!). Some of the other posts I ran across here helped me get an idea about how to solve it.

Here's what I did:
In the emergency shell, create a /mnt directory and mount the old root:
$:> mount /dev/mapper/isw_cafgghefcf_Volume0p1 /mnt

Then mount the virtual system directories:
$:> mount --bind /proc /mnt/proc
$:> mount --bind /dev /mnt/dev
$:> mount --bind /sys /mnt/sys

And change to your real system:
$:> chroot /mnt

(Here you can back up your files if you're worried and haven't done that yet)

Fix the boot issue:
$:> vi /boot/grub/menu.lst

In menu.lst, change the occurrences of the missing volumes to be the actual volumes found in /dev/mapper for both the root and the swap partitions.

$:> exit
$:> umount /mnt/sys
$:> umount /mnt/dev
$:> umount /mnt/proc
$:> umount /mnt

Reboot the system and you're back up and running!

If you aren't going to do anything but change the devices in menu.lst you don't have to go through the mounting of the system directories or the chroot, just mount your root filesystem and edit the menu.lst file (you won't have vi though unless you chroot).

---

