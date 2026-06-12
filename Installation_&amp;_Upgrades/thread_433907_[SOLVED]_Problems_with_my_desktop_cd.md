---
title: "[SOLVED] Problems with my desktop cd"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by waggygee on 2007-05-05
Today I downloaded the Ubuntu-6.06.1-desktop-i386.iso and copied it to a cd-r at 2x's speed. When it was done I attempted to boot off the cd as instructed. It all ran smoothly till a part were an Ubuntu logo was on my screen and the writting was... well, writting (the system was booting up). I couldnt help noticing that the bar under the Ubuntu logo had either significantly slowed down or stopped totally when it was written "Adding live CD user..." this stays on the screen for some time then it goes black and in white writting it reads:

Uncompressing Linux... ok, booting the kernel

Does anyone know what the problem might be? or more importantly how I could fix it or work around it?

---

### Post by jfinkels on 2007-05-05
> **waggygee said:**
> Today I downloaded the Ubuntu-6.06.1-desktop-i386.iso and copied it to a cd-r at 2x's speed. When it was done I attempted to boot off the cd as instructed. It all ran smoothly till a part were an Ubuntu logo was on my screen and the writting was... well, writting (the system was booting up). I couldnt help noticing that the bar under the Ubuntu logo had either significantly slowed down or stopped totally when it was written "Adding live CD user..." this stays on the screen for some time then it goes black and in white writting it reads:

Uncompressing Linux... ok, booting the kernel

Does anyone know what the problem might be? or more importantly how I could fix it or work around it?

Perhaps you don't have enough RAM? Maybe it's a hardware problem, what kind of specifications does your computer have?

You may want to try Xubuntu if you have an older computer.

---

### Post by aysiu on 2007-05-05
Could be...

1. Not enough RAM to run a live session
2. A corrupted download of the ISO

---

### Post by waggygee on 2007-05-05
no... Neither of those, I've got 1gb of ram and the CD works... I'll explain what just happened. When the earlier incident happened I had two harddrives (80gb nd 200gb), CD/DVD drive and floppy drive in my computer. This computer is for familly use so I decided to attept installing Ubuntu to a 20gb harddrive I 'liberated' from my dads old Mac. After reformating the hard drive (FAT) I unplugged all hard drives and floppy drive and plugged in the 20gb FAT HDD. So I ran Linux... and it worked... perfectly!! After happily playing around with the Ubuntu I decided to plug the hard drives back in. Once the other HDD's and floppy drive are in, the problem starts again.

---

### Post by waggygee on 2007-05-05
ok.... I tried running Ubuntu with my 200gb(NFST format) HDD unplugged, IT WORKS!! but when I attempt to open my other Windows based hard drive inorder to access my music and pictures, a window pops up reading:

Unable to mount the selected volume.
error: device/dev/hda1 is not removable
error: could not execute pmount

how could I fix this?

---

### Post by jfinkels on 2007-05-05
> **waggygee said:**
> ok.... I tried running Ubuntu with my 200gb(NFST format) HDD unplugged, IT WORKS!! but when I attempt to open my other Windows based hard drive inorder to access my music and pictures, a window pops up reading:

Unable to mount the selected volume.
error: device/dev/hda1 is not removable
error: could not execute pmount

how could I fix this?

Did you try to mount it using the "mount" command or with /etc/fstab? Is it ntfs formatted? If it is, you may need to use the ntfs-3g drivers before you can get read and write access. What is the output of the following command:
```

sudo fdisk -l

```

---

### Post by waggygee on 2007-05-06
After giving that comand I get this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24320   195350368+   7  HPFS/NTFS

and I still am unable to access anything

---

### Post by jfinkels on 2007-05-06
> **waggygee said:**
> After giving that comand I get this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24320   195350368+   7  HPFS/NTFS

and I still am unable to access anything

First you will need to mount the partition that you want to access. Take a look at this thread where I describe how to do this. [http://ubuntuforums.org/showthread.php?t=434236](http://ubuntuforums.org/showthread.php?t=434236)

Next, to read and write on NTFS partitions, you may need the NTFS-3G drivers. To install them, type the following:
```
sudo aptitude install ntfs-config
```

And then run the following command to enable read and write access:
```
sudo ntfs-config
```

Then you will be able to read files in the directory in which you mounted the partition and write to these directories if necessary.

---

### Post by waggygee on 2007-05-06
E: couldn't find package ntsf-config

---

### Post by jfinkels on 2007-05-06
> **waggygee said:**
> E: couldn't find package ntsf-config

First it should be "ntfs-config" not, "ntsf-config". NTFS stands for New Technology FileSystem, I believe. It's an initialism.

Second, come to think of it, you may have to enable extra software repositories. Go to "System > Administration > Software Sources" and check the box next to the "universe" repository. THEN follow the rest of the directions.

---

### Post by waggygee on 2007-05-06
I do not see "software sources" where you directed me... Is there an alternative root or way to access it?

---

### Post by jfinkels on 2007-05-06
> **waggygee said:**
> I do not see "software sources" where you directed me... Is there an alternative root or way to access it?

It may be named something else in Ubuntu 6.06 maybe "Software Repositories" or something similar? Well, if it's not there,try typing the following command in the terminal to open the "Software Sources" dialog:
```

gksudo /usr/bin/software-properties-gtk

```

If that doesn't work, there's another slightly more difficult way.

1. Make a backup copy of your /etc/apt/sources.list file by typing the following:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

2. Open the file /etc/apt/sources.list:
```

gksudo gedit /etc/apt/sources.list

```

3. Edit the file so that the line that looks like this, which includes "universe":
```

# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

```
has no hash "#" in front of it, so it will look like this:
```

 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

```

4. Save the file, and update your sources.list file by running the following command:
```

sudo aptitude update

```

5. Now try to install ntfs-config:
```

sudo aptitude install ntfs-config

```

---

