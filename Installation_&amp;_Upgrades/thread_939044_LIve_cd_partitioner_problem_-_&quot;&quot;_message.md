---
title: "LIve cd partitioner problem - &quot;???&quot; message"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by merlo on 2008-10-05
I had ubuntu installed happily and then I repartitioned my hard drive to do a dual-boot with slackware and ubuntu.

When I run the ubuntu live cd installer it hangs at the partitioner and displays a message box which says "??? ???" 

I have an official ubuntu cd and the problem is not with that because it  installs fine on another computer.

I am now able to install slackware without a problem but can't install ubuntu because I can't get ubuntu to see my partition table.

Here is my fdisk info from the live cd:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00036621

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      489951   83  Linux          /boot
/dev/sda2              62         304     1951897+  82  Linux          swap
/dev/sda3             305        1520     9767520   83  Linux         /(slack)
/dev/sda4            1521        3050    12289725   83  Linux          (for ubuntu root)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


Any help would be very much appreciated.

---

### Post by ikaps on 2008-10-18
Hi,
Is your problem solved? I am asking, because I have the same problem - I get "??? ???" message during install 8.10 on my Toshiba a45 laptop.
The CD (alternate) is good, as I have successfully installed 8.10 on another laptop.

---

### Post by Sef on 2008-10-18
> Hi,
Is your problem solved? I am asking, because I have the same problem - I get "??? ???" message during install 8.10 on my Toshiba a45 laptop.
The CD (alternate) is good, as I have successfully installed 8.10 on another laptop.

CD may be bad now.

> I had ubuntu installed happily and then I repartitioned my hard drive to do a dual-boot with slackware and ubuntu.

When I run the ubuntu live cd installer it hangs at the partitioner and displays a message box which says "??? ???" 

I have an official ubuntu cd and the problem is not with that because it  installs fine on another computer.

1. CD may be bad now.

2. Try [gparted]("http://gparted.sourceforge.net").

---

### Post by merlo on 2008-10-20
No, I didn't solve the problem. I tried manually repartitioning several times to increasingly simple partition arrangements but couldn't get the live partitioner to see anything until I just wiped the whole harddrive and then it worked fine. So I just have ubuntu again on that computer. So the cd is still good.

On my other computer I tried adding slackware as a second distro to ubuntu and had different problems and also gave up. No-one told me it was harder to dual boot 2 linux systems!

---

### Post by ikaps on 2008-10-20
Yesterday I tried to install another Ubuntu 8.04 from liveCD and... I got the same error! So now I'm sure the CD is not the problem.

---

### Post by merlo on 2008-10-20
Yes. I guess the error is in not partitioning correctly.
I am very inexperienced with partitioning. I'll try and do it again properly when i have time.
Good luck. If you work out the answer please post it.

---

