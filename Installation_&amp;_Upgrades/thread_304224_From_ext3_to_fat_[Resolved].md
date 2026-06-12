---
title: "From ext3 to fat [Resolved]"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by robytex on 2006-11-21
How can I do to format a ext3 partition (empty) to FAT o FAT32
without reistall ubuntu?
This partition is dedicated only to personal data.
TIA

Robytex

---

### Post by taurus on 2006-11-21
Boot with the LiveCD and use gparted from it to reformat that empty partition to fat32...

---

### Post by robytex on 2006-11-21
I've installed gparted from the repository but the format option
is grey.
Isn't possible to do it so? Only from live cd?
TIA

Robytex

---

### Post by taurus on 2006-11-21
It's best to do it from a LiveCD!!!  Otherwise, you can download GParted LiveCD if you don't have the Ubuntu one...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by ajgreeny on 2006-11-21
You should be able to do it with gparted from the repos, but you must make sure that the partition is unmounted before you do anything to it.

---

### Post by robytex on 2006-11-22
Ok, I've unmounted the partition, formetted in FAT32 with
gparted and now.....how can i do to mount it again?
I know....I'm a beginner.....

TIA

Robytex

---

### Post by taurus on 2006-11-22
What's the output of these two command from a terminal?

```
sudo fdisk -l
```

---

### Post by robytex on 2006-11-22
This is the output

-------ytex-desktop:~$ sudo fdisk -l

Disk /dev/hda: 12.7 GB, 12749635584 bytes
255 heads, 63 sectors/track, 1550 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1               1         639     5132736   83  Linux
/dev/hda2             640         770     1052257+  82  Linux swap / Solaris
/dev/hda3             771        1550     6265350    b  W95 FAT32
------bytex-desktop:~$ 

and now?
Thanks

---

### Post by aysiu on 2006-11-22
Paste these commands in the terminal: ```
sudo mkdir /media/*extra*
sudo nano -B /etc/fstab
``` Add this line to the end of the file and make sure there are no other lines that refer to /dev/hda3 (you can delete lines by pressing Control-K): ```
/dev/hda3 /media/*extra* vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter) and ```
sudo mount -a
``` This will mount /dev/hda3 to a directory called *extra*, which should appear on your desktop. If you want it called something else, just change *extra* to something else in all the instructions I gave.

---

### Post by robytex on 2006-11-22
FANTASTIC!!!!
It works.
Now I'll try to understand what I've done with the command you
suggested to me.
THANK YOU VERY MUCH!!

Roby

---

### Post by aysiu on 2006-11-22
I'll sum it up for you:

Make a folder where you can access /dev/hda3

Edit the /etc/fstab file while also creating a backup for it

Let /etc/fstab know you have a FAT drive you want to appear in a folder and which folder you want it to appear in

Mount all drives in their appropriate folders

---

