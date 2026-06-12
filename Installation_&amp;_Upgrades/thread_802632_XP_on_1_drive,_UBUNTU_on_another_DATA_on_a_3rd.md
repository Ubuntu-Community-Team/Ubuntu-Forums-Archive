---
title: "XP on 1 drive, UBUNTU on another DATA on a 3rd?"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by gmilne on 2008-05-21
Is this feasible? If so How would I set about it. Running 7.10
I also need to know 
1. Can a Drive with multiple partitions have different formats eg. 1 parition NTFS another ext3 and another partition FAT32

Which formats would be best for my setup given that I want to read and write data from linux and XP

thanks

---

### Post by Pumalite on 2008-05-21
A drive can have partitions with different formats. Linux reads and write to ntfs. You can see Ubuntu from XP with a special driver. I hope you have all SATA or all IDE.

---

### Post by IHATEDLINK on 2008-05-21
Yeah, sure. A Drive with multiple partitions CAN have different formats.
It's actually very easy to do it.
For dual-booting use [THIS]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") 

After you finish, boot in to Ubuntu and do this:

1. Open terminal

2. Type: 
```
sudo apt-get gparted
```

Type your password.
This will install Gnome Partition Editor (Gparted)

3. After the installation is over do to Settings>Administration> Gnome Partition Editor and create a new partition for your Data. Make sure this partition is formated as FAT32 so both Ubuntu AND Windows can read/write on it.
Thats pretty much it.
Remember: NTFS for XP, ext3 for Ubuntu and **FAT32 for DATA.**
DATA can be also used as a "sharing folder" between the OS' cause Windows can't read/write on ext3 but both OS' can write and read in FAT32.
As Pumalite points out, there are a few drivers available for windows to read and write in ext2/ext3. They work great, I tested them myself.

Remember to THANK ME by clicking the little star button at the bottom-right of the post if it was useful :)

---

### Post by Pumalite on 2008-05-21
Better use Gparted Live CD to do your partitioning:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by gmilne on 2008-05-22
In the message from IHATEDLINK, the site you recommended assumes I installed Linux first. I installed XP first. Trying Gparted instead.
Thasnk

---

### Post by IHATEDLINK on 2008-05-24
Well... How did it went?
For a guide about Dual-booting with XP FIRST go [HERE]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
Pumalite is right, you better use the gParted live CD or Ubuntu Live CD itself (Once it booted System>Administration>Gnome Partition Editor)
If you still want the XP-can-read-ext3 drivers go [HERE]("http://www.fs-driver.org/")

Oh, and if you installed gParted and you want to get rid of it:

```
 sudo apt-get remove gparted 
```

Tell me how it went later.

---

