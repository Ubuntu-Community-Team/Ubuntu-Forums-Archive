---
title: "Ubuntu 10.04 won't recongnize its root HDD after motherboard change"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by iron4o on 2013-01-25
So yesterday I changed my motherboard to Asus P877-V and now my Ubuntu 10.04 won't boot at all. Grub works fine (more on that later) but when selecting to boot the 10.04 it ends up in initramfs saying "Drive with UUID <its uuid> cannot be found". This is the strangest thing since that is the drive it is booting from!

Anyway, heres what exactly the upgrade was: I changed the motherboard, CPU and added two new hard drives. The old drive (which has the Ubuntu OS on it) is connected to the 3Gps SATA and the new ones are 6Gbps.

Some more facts about the setup:

 * The BIOS recongizes the disk fine and I boot from it in non-UEFI mode.
 * I also have Windows 7 on the same disk and it boots fine.
 * Booting from 12.04 LiveCD I can mount the drive and modify it at will.
 * The drive is partitioned

What I did try up to this moment:

 * Reinstalled Grub. At first I thought that it might be some boot params problem. So from the LiveCD I reinstalled Grub - no change.
 * After that I found [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") . I tried it and (surprise surprise!) it reinstalled Grub. But aside from that it produced a lot of boot information for my system  - [http://paste.ubuntu.com/1564093/](http://paste.ubuntu.com/1564093/) . The UUID - 0670059a-e45c-440e-98f2-79bae707e593

I don't have the slightest idea what to do now. Installing newer Ubuntu is not an option at the moment.

---

### Post by sanderj on 2013-01-25
And if you boot 10.04 from a live Ubuntu-stick/CD ... does it work? 
Reason: is Ubuntu 10.04 compatible with your new mobo ... ?

---

### Post by Mark_in_Hollywood on 2013-01-25
I have never had your problem. So, take this with a grain of salt.

[http://forum.avsim.net/topic/391342-asus-p877-v-pro-sata-drive-problem/](http://forum.avsim.net/topic/391342-asus-p877-v-pro-sata-drive-problem/)

I found this by netsearching for: 

asus p877-v drive not found

---

### Post by Hakunka-Matata on 2013-01-25
Open a Terminal and list all current partition UUIDs ```
sudo blkid
```
next list your /etc/fstab file ```
cat /etc/fstab
```and compare the UUIDs, you'll probably find that they do not agree, because new UUIDs have been generated on first boot of new hardware.

If this is true, then you must edit the fstab file to agree with the new UUIDs.

---

### Post by iron4o on 2013-01-25
The UUIDs in fstab are exactly the same as those reported in the 12.04 LiveCD. I did try to remove the swap partition from fstab as initially I suspected it to be source of the problem. Sadly it was not.

Next thing I will try 10.04 LiveCD and list you fstab and reported UUIDs anyway.

---

### Post by iron4o on 2013-01-25
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: LABEL="Storage-2" UUID="E89883AF98837AB8" TYPE="ntfs" 
/dev/sdb2: LABEL="Storage-1" UUID="EABC75D1BC759931" TYPE="ntfs" 
/dev/sdc1: UUID="D0B09B49B09B34C6" TYPE="ntfs" 
/dev/sdc5: UUID="1CECDA9DECDA710E" TYPE="ntfs" 
/dev/sdc6: UUID="c24d8de6-7b17-41b8-aae1-32de29fe2e61" TYPE="swap" 
/dev/sdc7: UUID="0670059a-e45c-440e-98f2-79bae707e593" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc8: UUID="df196da3-591a-480d-8c04-f09ff88c2316" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="PENDRIVE" UUID="1AF7-254F" TYPE="vfat" 

```


```
ubuntu@ubuntu:~$ cat /media/0670059a-e45c-440e-98f2-79bae707e593/etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0670059a-e45c-440e-98f2-79bae707e593 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=df196da3-591a-480d-8c04-f09ff88c2316 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=c24d8de6-7b17-41b8-aae1-32de29fe2e61 none            swap    sw              0       0
UUID=1CECDA9DECDA710E /media/sda5 ntfs defaults 0 2
```

Making bootable 10.04 will require some time though. I hope it boots :D

---

### Post by darkod on 2013-01-25
The bootinfo shows the boot files are towards the end of the disk. This is sometimes an issue but with older boards. If the board is relatively new it shouldn't have a problem.

The thing is that some bioses can't locate boot files beyond 137GB on the disk, and in your case they are beyond this point.

Unfortunately there is no easy way to check this that I know of, and no easy way to repair it if it does turn out to be your problem. You will have to shrink the first partition on the disk in order to create a small /boot partition there. That way the boot files will always be at the start of the disk.

Except this, I have no other ideas since the UUID is correct, the bootinfo shows that. Actually a few weeks back I did the same, swapped my board, memory and cpu. Simply plugged the same ssd I was using with the old board and it worked fine, without touching literary anything.

You can also try plugging the disk in a different port, like one of the SATA3 ports even if the disk is SATA2. Often SATA2 and SATA3 ports can be on different controllers on the board and it can make a difference. Even though it's supposed to work in any port, sometimes it doesn't for various reasons.

---

### Post by iron4o on 2013-01-25
Thanks, darkod.
The thing that boggles me is that it does seem to boot to some point. To the point which initramfs is loaded anyway. Doesn't that mean it actually started loading the kernel? Or it is a GRUB thing?

---

### Post by darkod on 2013-01-25
> **iron4o said:**
> Thanks, darkod.
The thing that boggles me is that it does seem to boot to some point. To the point which initramfs is loaded anyway. Doesn't that mean it actually started loading the kernel? Or it is a GRUB thing?

I don't know the details of the boot process but I don't think the message "UUID cannot be found" is very far from the beginning of it.

---

### Post by Hakunka-Matata on 2013-01-25
Since you can 'select' the 10.04 boot option, have you tried editing it to see if anything looks fishy in the details?  Like UUID?

---

### Post by iron4o on 2013-01-28
When editing the GRUB menu entry - there is the correct UUID.
Also, Ubuntu 10.04 LiveCD boots. I would try to copy the whole partition somewhere else and see if it works from that other drive. Will make sure it is at the beginning of it.

---

### Post by oldfred on 2013-01-28
Related to your first answer post #2. Someone previous posted this on Asmedia ports. It seems to be a common issue with ASmedia ports?

> Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.
    

---

