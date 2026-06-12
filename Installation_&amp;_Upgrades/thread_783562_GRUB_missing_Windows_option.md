---
title: "GRUB missing Windows option"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2008-05-05
I had Windows XP Home on my Dell Latitude D600 laptop. I decided to install Ubuntu 8.04 so it will dual boot. 

After installation of Ubuntu, when I restart, I only see Ubuntu boot options.

So I added the following into my
```

/boot/grub/menu.lst

```

```

title Windows XP Home
rootnoverify (hd0,2)
makeactive
chainloader +1

```

After I restart, the WIndows boot option is visible, however it give the following error if I choose it:
```

Error 12: Invalid Device Requested (hd0,8)

```
Apparently, I am not having it set up correctly.


My partitions look like
```

$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1580    12691318+  83  Linux
/dev/sda2            1581        7296    45913770    f  W95 Ext'd (LBA)
/dev/sda5            3825        7296    27888808+   7  HPFS/NTFS
/dev/sda6            1581        1762     1461852   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Any help, suggestions are appreciated.

---

### Post by tamoneya on 2008-05-05
windows would probably be on /dev/sda5  since this is the NTFS partition.  The other one (/dev/sda2) is a FAT32 and it wouldnt be located there.  Also grub numbers drives and partitions with a 0 indexed system so sda5 = (hd0,4).  In other words try this.```
title Windows XP Home
rootnoverify (hd0,4)
makeactive
chainloader +1
```
If that doesnt work post your entire menu.lst so we can search for other possible errors.

---

### Post by Pumalite on 2008-05-05
You are trying to boot Windows from a logical partition. Windows needs a primary partition. Start from scratch and install Windows in a primary partition; preferably sda1. Install Ubuntu last.

---

### Post by Physicist on 2008-05-05
How do you know it is not on a primary partition ?

In other words, how do I correctly understand
```

$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1580    12691318+  83  Linux
/dev/sda2            1581        7296    45913770    f  W95 Ext'd (LBA)
/dev/sda5            3825        7296    27888808+   7  HPFS/NTFS
/dev/sda6            1581        1762     1461852   82  Linux swap / Solaris

Partition table entries are not in disk order

```

* I had Windows installed on the computer before installing Ubuntu. Is it possible for Windows to be on a logical partition but not a primary one?

* Is it possible for some reason that fdisk did not list all my partitions, especially the one with Windows ?

---

### Post by Pumalite on 2008-05-05
Let's find out. Post a screenshot of gparted

---

### Post by tamoneya on 2008-05-05
try changing menu.lst as i mentioned above.

---

### Post by fmartinez on 2008-05-05
> **Physicist said:**
> How do you know it is not on a primary partition ?

In other words, how do I correctly understand
```

$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1580    12691318+  83  Linux
/dev/sda2            1581        7296    45913770    f  W95 Ext'd (LBA)
/dev/sda5            3825        7296    27888808+   7  HPFS/NTFS
/dev/sda6            1581        1762     1461852   82  Linux swap / Solaris

Partition table entries are not in disk order

```

* I had Windows installed on the computer before installing Ubuntu. Is it possible for Windows to be on a logical partition but not a primary one?

* Is it possible for some reason that fdisk did not list all my partitions, especially the one with Windows ?

Alright, so from what I understand... 
- You had WinXP 
- You install Ubuntu as dual boot
- Now you can't boot into WinXP
       - If this is correct and with the output of you menu.lst file. As suggested before all you have to do id edit your menu.lst file to point to the /dev/sda5 (This should be your WinXP Partition). The other partition (/dev/sda2) should be your recovery partition of WinXP. 
- You SHOULD NOT need to reinstall Windows. 
Good Luck.

---

### Post by Pumalite on 2008-05-05
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

### Post by Physicist on 2008-05-05
My gparted screenshot: screenshot.png

---

### Post by Pumalite on 2008-05-05
Sorry, but that's a logical partition inside of an extended one. Better start over. Don't knock your head against a wall.

---

### Post by Physicist on 2008-05-05
Can you give more specific instructions ?

Do you mean I can keep Ubuntu and have to reinstall Windows ?

What partions should be erased when I reinstall Windows ?

Can I avoid reinstall Ubuntu ?

What I did wrong in the installation of Ubuntu so I have to reinstall Windows now ?

---

### Post by Pumalite on 2008-05-05
I don't know what you did, but that scheme will never work. Better save your data and reformat your hard drive. Use Gparted Live CD; make a first partition formatted ntfs at the beginning of the drive (sda1) A second one for Ubuntu formatted ext3 if you want. Install Windows first in sda1. Install Ubuntu last.

---

### Post by fmartinez on 2008-05-05
> **Physicist said:**
> Can you give more specific instructions ?

Do you mean I can keep Ubuntu and have to reinstall Windows ?

What partions should be erased when I reinstall Windows ?

Can I avoid reinstall Ubuntu ?

What I did wrong in the installation of Ubuntu so I have to reinstall Windows now ?

Why don't you give us a step by step break down of what you did when you installed Ubuntu? 
Start from the point where you ONLY had WinXP installed; NO UBUNTU!
Maybe we can help determine what you did wrong.

---

