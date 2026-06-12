---
title: "[Removing] Ubuntu"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Choxo on 2007-01-31
Hey All,

Might be a wierd question, but what I want to do is this:
[LIST=1]
[*] remove ubuntu completely
[*] install windows
[*] create partition with Gparted boot CD
[*] Install Ubuntu on second partition.
[/LIST]

I tried to add a entry in grub menu like this:
```

title           Microsoft Windows XP Professional
root           (hd0,0)
makeactive
chainloader     +1

```


But I got a STOP error when I try to install it... (this one:)
***stop 0x0000007E ( oxc 0000005, oxf9a380bf, oxf9e84208, oxf9e834208, 0xe9e83f08

*** PCI.SYS address f9a380bf base at f9a31000, date stamp 3b7d8ssc

sudo fdisk -l gives me this:

```

spitz@spitz:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29638   238067203+  83  Linux
/dev/sda2           29639       30394     6072570    5  Extended
/dev/sda5           29639       30394     6072538+  82  Linux swap / Solaris

```


I know it's strange to first remove ubuntu & then install it again, but I 've got my reasons...

Thanks anyway!

---

### Post by jenks on 2007-01-31
Hello,

  I'm not sure why you're working on grub already. It seems to me that all you need to do (once you completely back up your data off your hard drive) is boot to the ubuntu live CD, delete the partitions on your hard drive with gparted, and then install windows, which should partition and format the drive. Then reinstall ubuntu and manually partition, resizing the windows partition down and adding the swap and root partitions. I would hope that the ubuntu install handles setting up the dual boot for you, so that you won't have to grub around in grub. ;-)

  Yours,

    Chris

---

### Post by housam on 2007-01-31
-Back-up every thing
-Boot from the live CD 
-Use Gparted to delete the entire HDD,then to repartition it into 4 partitions :
   - ntfs for windows 
   - ext3 for ( / ) root
   - swap fpr swap partition ( 1 Gb )
   - ext3  for /home 
-install windows
-install ubuntu ( when it comes to the partition question , choose the manual way)

You will get a dual boot.

Good luck

---

