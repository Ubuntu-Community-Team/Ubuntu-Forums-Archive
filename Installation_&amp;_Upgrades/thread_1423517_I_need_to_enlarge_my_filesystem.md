---
title: "I need to enlarge my filesystem"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by lateralus01 on 2010-03-06
I built a distro from scratch for my xbox.  I partitioned a usb stick and built it on there first.  To transfer the filesystem, I used a bootdisk that ran on my xbox and just used dd:
```

dd if=/dev/sda3 of=/dev/hda3

```

The problem is, the usb stick was only 2GB while the partition I made for linux on my xbox filesystem is 5GB.  I've ran out of space already and I know I haven't used 5GB which leads me to believe that the ext3 filesystem on my partition isn't 5GB but is instead the 1.5GB that it was on my usb stick.  How do I enlarge it to fill the partition?

thanks,
lateralus01

---

### Post by johnson.d on 2010-03-08
If your distro has Gparted built into it, you can use that for enlarging your partition to 5 GB.

After installing GParted you can resize the partition by using the following steps:
1) Boot the machine using the USB stick.(You cannot resize the partition that is mounted,and your hard-disk mounts while the OS boots from it.)
2) Run Gparted
3) After it shows the partition details of the particular Harddisk right click on the partition and click on Resize/Move.
4) On the partition represented graphically, click on the End of the partition and drag it till the end if you want to use the whole space for the same partition.
5) Click apply.

Now check whether the partition uses 5GB fully.

If you Run OS without graphical interface, you can use parted instead.

You can download parted from the following link:

[http://www.gnu.org/software/parted/download.shtml](http://www.gnu.org/software/parted/download.shtml)

You can find the parted manual from the following link:

[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

---

