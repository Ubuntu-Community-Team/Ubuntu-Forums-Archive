---
title: "&quot;No root file system defined&quot; Ubuntu 10.04 LTS 64-bit"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by Dymium3 on 2011-12-11
Okay, so I've been spending this whole day trying to install Ubuntu. First I tried Wubi. After everything installed and I booted into Ubuntu, it displayed "No root file system defined Please correct this from the partitioning menu." I was forced to do a manual power off. I spend hours searching the forums but to no avail. I eventually decided to do a "real" install by partitioning my hard drive inside the install CD. After loading it and going through a few pages, I arrived at the partitioning menu. There was nothing displayed in the table and clicking forward caused the "No root file system defined" error.

I can provide system specs/logs/pictures if needed.

---

### Post by Rubi1200 on 2011-12-11
Hi and welcome to the forums :-)

Please check in the Windows Disk Management utility whether the disks are labeled as Basic or Dynamic.

If the latter, you would be advised not to try and install Ubuntu as there is a risk of data corruption.

Post the specs. anyway and check the integrity of the image and that you burned at the lowest speed.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by fdrake on 2011-12-11
on a live cd/usb , opne the terminal an type:
```

sudo fdisk -l

```
and post here the output.
if you see SFS filesys type it means you have a win dynamic extended partition... you cannot use wubi in this case but you can try with the real install by moving around some space.. the buckup for the later option is [COLOR="Red"]**_HIGHLY_**[/COLOR] suggested because there is a good change that Grub may not be able to launch win.

---

