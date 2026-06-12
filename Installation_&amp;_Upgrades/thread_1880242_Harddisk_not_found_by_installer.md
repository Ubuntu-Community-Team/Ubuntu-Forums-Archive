---
title: "Harddisk not found by installer"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by socken23 on 2011-11-13
Hi all

I'm trying to install Xubuntu or Lubuntu on my desktop. I boot from a USB stick which works great, the Live-CD works without any problem. If I run gparted, I see my 250GB harddisk, I can re-partition it, delete partitions without a problem.
When I start the installer though, the harddisk somehow is not found correctly.
When I reach the screen "Installation type" where I'm supposed to create the partitions, it's just empty.
In the dropdown for the bootloader, it correctly shows me /dev/sda. 

How can I fix this?

sudo fdisk -l shows me something like this:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18fc82b1

Device Boot  Start        End    Blocks   Id  System
/dev/sda1    2048   488396799 244197376   83  Linux

```

and then some information about the USB stick.

Any idea?

---

### Post by 2F4U on 2011-11-13
Is this an empty hard disk or do you already have partitions on it. Are you using the automatic partitioning? If yes, can you try the manual partitioning, which is labelled "something else"?

---

### Post by BillyBoa on 2011-11-13
Try to format the disk and check it for errors. 

see here I think you can helped

[http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu](http://superuser.com/questions/15916/is-there-a-chkdsk-equivalent-available-for-ubuntu)

---

### Post by ankspo71 on 2011-11-13
Hi,
It might be that your hard drive is being falsly detected as a raid setup.
[http://ubuntuforums.org/showthread.php?t=1870478](http://ubuntuforums.org/showthread.php?t=1870478) (see post 10)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/878568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/878568)

Notice the screenshots provided in the bug report:
[https://launchpadlibrarian.net/83225344/UbiquityLockUp.png](https://launchpadlibrarian.net/83225344/UbiquityLockUp.png)
[https://launchpadlibrarian.net/83227661/Disk%20Utility%20Image.png](https://launchpadlibrarian.net/83227661/Disk%20Utility%20Image.png)

While using your Live CD, install and use "gnome-disk-utility" to see if your drive or partitions is being falsly shown as a "Raid Component", then erase the partitions if they are, then try running the Xubuntu installer again and see if the installer will allow you to partition your drive and complete the installation.

---

### Post by socken23 on 2011-11-13
Thanks all for your tipps. I tried different things, no partitions at all, one ext4 partition taking up the whole space, nothing worked.
ankspo71s tipp was perfect, thanks a lot!!
Exactly the problem I was having. I got the exact same screens you've posted from the bug report.

Using the gnome-disk-utility to format the disk solved the problem.
On with the installation :guitar:

Thanks a lot

---

