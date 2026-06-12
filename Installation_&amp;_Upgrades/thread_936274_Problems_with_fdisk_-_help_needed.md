---
title: "Problems with fdisk - help needed"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by XBrown on 2008-10-02
I have a 30gb, and 320gb hard disks.  Master and slave, respectively.  Ubuntu boots (albeit slowly) from the smaller drive.  It recognizes the second disk, but it says it is read-only.  When I try to change it, it says I don't have permission.  I want to reformat the larger drive, and start over fresh.  When I run ($ fdisk /dev/hdb), it comes back with a message saying:

Unable to open /dev/hdb
xavierbrown@garage:~$

I have very little experience with linux, so step by step instructions would be greatly appreciated.

If I can ever reformat this thing, what file system do you recommend?

---

### Post by caljohnsmith on 2008-10-02
It would probably be easier to just use Ubuntu's partition editor to format your larger HDD; press ALT + F2, and enter:
```
gksudo gparted
```
Then select your large HDD, delete any partitions that are there, create however many new partitions you want (even if it is just one single partition for the whole HDD), and format them however you want. If you are only going to be accessing the large HDD from Ubuntu, you could use ext3 as the file system. If you have Windows and want to access the HDD from Windows and Ubuntu, you could use NTFS or FAT32 for the file system. Let me know if you need more details, I'll be happy to help if I can.

---

### Post by mikewhatever on 2008-10-02
You probably need sudo to use fdisk. An easier option is to use GParted Live CD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by dabl on 2008-10-02
If I understand correctly, there is no data that you care about on either hard drive.  If true, then (using the OTHER computer) download the GParted Live CD image from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

and burn it to a CD. Using that CD to boot, partition and format the 30GB drive as ext3, except for a 1GB swap partition.  Set the "boot" flag on it.

Partition the 300G into a single partition and format it ext3. Make sure the boot flag is NOT set.

Then boot your Ubuntu CD and install it on the 30GB drive.  After it is installed and booting correctly, you can edit /etc/fstab to add the other drive for automatic booting.

---

### Post by Sef on 2008-10-02
> If I understand correctly, there is no data that you care about on either hard drive. If true, then (using the OTHER computer) download the GParted Live CD image from here:

[http://sourceforge.net/project/showf...kage_id=271779]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779")

and burn it to a CD. Using that CD to boot, partition and format the 30GB drive as ext3, except for a 1GB swap partition. Set the "boot" flag on it.

Partition the 300G into a single partition and format it ext3. Make sure the boot flag is NOT set.

Then boot your Ubuntu CD and install it on the 30GB drive. After it is installed and booting correctly, you can edit /etc/fstab to add the other drive for automatic booting.

The GParted Live CD is a newer version than what is found on the Ubuntu Live CD.

---

