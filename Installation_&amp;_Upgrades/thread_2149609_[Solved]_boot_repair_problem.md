---
title: "[Solved] boot repair problem"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by itajaja on 2013-05-29
[FONT=arial]Hello,
[/FONT]
[FONT=arial]I had two partitions on my pc, two linux distros on two ext partitions (sda1 and sda3). I decided to install win8 replacing one of these partitions. Then I used a live usb to repair the grub with boot repair, but I noticed that the parition got messed up. Here is the boot info: [http://paste.ubuntu.com/5713190/](http://paste.ubuntu.com/5713190/)
[/FONT]
[FONT=arial]Somehow it happened somehting also to the other partition. Do you know what I can do?
Thanks :)[/FONT]

---

### Post by DanielGerep on 2013-05-29
My guess is that you have no logical partition and they are overlapping each other.

You can check your fdisk -l and see the message: "**Partition 3 does not start on physical sector boundary.**"

There is no Linux partition, just the swap.

I have Windows 7 and Ubuntu installed, here is my fdisk -l:


```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b555

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   206579711   103186432    7  HPFS/NTFS/exFAT
/dev/sda3       206581758  1953523711   873470977    5  Extended
/dev/sda5       206581760  1941231615   867324928   83  Linux
/dev/sda6      1941233664  1953523711     6145024   82  Linux swap / Solaris
```

I'm new to it, so it's just a guess =)

---

### Post by itajaja on 2013-05-29
but there was a linux in sda3, no doubt about it...

---

### Post by fantab on 2013-05-29
Your /dev/sda3 is an EXTENDED Partition. An Extended partition is not exactly a partition but a 'container' which contains LOGICAL Partitions. As such, an extended partition will not have any data. It is likely that you had linux on /dev/sda1 and /dev/sda2 but it is impossible to have any on /dev/sda3. 

If you want to dual boot Linux/Ubuntu and Windows 8 then it will be better and easier to 'start all over again'. If you are agreeable to this then we need some more information about your machine. And tell us how do you want your operating systems set up?
If you Bios is EFI capable? etc.

---

### Post by itajaja on 2013-05-29
Yes is EFI capable, but the partitions weren't EFI. The problem is that i CAN'T LOSE the linux partition that I had. There are too many things on it, and the configuration of the OS itself would take weeks to be done again (was very fine tuned) so I am willing to do everything is possible to restore it. The EXT partition contained a logical linux partition, 100% sure. If you need additional information please ask :)
Thanks

---

### Post by itajaja on 2013-05-29
Here it's a disk utility screenshot [http://d.pr/i/M1Ff](http://d.pr/i/M1Ff). For some reason, the part of the hard disk labeled as "Free 251 GB" contained linux before the Windows installation. There is also the warning message that probably is related to the problem. Any help is really appreciated, there was a lot of vital things in that partition...

---

### Post by fantab on 2013-05-29
Okay, try **[FIXPARTS]("http://www.rodsbooks.com/fixparts/")**, and see if can help correct the partition error. It should. And if your Linux partition is readable again then.. you can back up or rescue your data even if the OS on the partition is un-bootable, using Live Ubuntu DVD/USB.

If the DATA on the partition appears to be lost then Try **[TESTDISK]("http://www.cgsecurity.org/wiki/TestDisk")**, it should recover most of your DATA. Check the 'size' of the files/folders you want to recover. If its 0bytes then the data is lost.

Good Luck...

EDIT: Your Disk Utility image shows that the HDD has 'some bad sectors', you may have to rectify that as well. But first try to rescue your DATA.

---

### Post by itajaja on 2013-05-29
I used testdisk to reenable the linux partition, I also deleted the windows partition, it seemed to work perfectly. At least I was able to mount the disk and backup the file. But as I said I would like to restore also the OS. so I used the boot repair again, this is the outcome: [http://paste.ubuntu.com/5714279/](http://paste.ubuntu.com/5714279/) getting the error contained in the link.
From Gparted I can see that now the partition is labeled as boot, but the system doesn't boot anyway. What am I missing?

---

### Post by fantab on 2013-05-29
> **itajaja said:**
> but there was a linux in sda3, no doubt about it...

> **itajaja said:**
> I used testdisk to reenable the linux partition, I also deleted the windows partition, it seemed to work perfectly. At least I was able to mount the disk and backup the file. But as I said I would like to restore also the OS. so I used the boot repair again, this is the outcome: [http://paste.ubuntu.com/5714279/](http://paste.ubuntu.com/5714279/) getting the error contained in the link.
From Gparted I can see that now the partition is labeled as boot, but the system doesn't boot anyway. What am I missing?

I suspect that by removing/deleting partitions, the partition numbers got changed, perhaps even UUIDS. However, I am not exactly sure.
For instance your SWAP was earlier on /dev/sdb5 or /dev/sdb6 but now its /dev/sda2. Similarly your '/' partition also changed. I can't tell if UUIDS also changed. 

It will be wise to save your important DATA and reinstall, there could be other possible errors as well. 

You can try booting with a Live CD/USB mount your ext4 partition, open /etc/fstab and make necessary adjustments with UUIDS and Labels. If that doesn't work then, "Reinstall" it is.

Good Luck...

---

### Post by itajaja on 2013-05-29
You think there is no way to create a grub loader that fits this configuration from scrath? Basically the question is the following: given only a partition with an OS, is it possible to make it bootable?

---

### Post by fantab on 2013-05-30
Try Boot-Repair to reinstall GRUB to /dev/sda. To do this choose from Boot-Repair, 'Advanced options' and choose "Reinstall Grub". Then 'Grub Location', choose 'sda'. Run Boot-Repair. If if fixes it good otherwise....

---

### Post by itajaja on 2013-05-30
I solved it. I used boot-repair, and i selected the option purge GRUB. It removed completely grub and reinstalled it. Thank you very much for your support!!!! ;)
P.s: hey, how do I put [solved] in the thread title?

---

### Post by fantab on 2013-05-30
Glad you got it. 
I think we have to EDIT the first post and from the dropdown list choose '[Solved]'.

---

