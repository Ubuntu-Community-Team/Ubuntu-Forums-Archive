---
title: "error with partition in installation"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by skate2 on 2012-02-05
hi
(first i apologize for my bad english language grammer)

i have a windows7 in my computer.
my partition is:
[IMG]http://www.novinupload.com/uploads/13284604941.jpg[/IMG]

whene i try to install ubuntu on mylaptop, i get error in "checking storage part".
it means u just see the one partition (just my harddisk)that i cant edit , add, create new table.

for solving this problem, i tried:
_i change hdd type in my bios, from ata to AHCI
_create ext3 partition(from windows)
_create swap format partition(from windows)
_run gparted, but still see just my harddisk
_create unlocated disk

But my problem didnt solve.
---------------------------------
one point is i can access my windows partition from liveubuntu

plz help me dude

---

### Post by sudodus on 2012-02-05
Welcome to the Ubuntu Forums skate2 :-)

I suggest that you try ***Gparted*** when you have booted your computer from your Ubuntu install CD or USB drive. And report what you can see from that! [COLOR="Red"]Only look at the drive[/COLOR], do not edit anything yet! Also start to [COLOR="red"]prepare by backing up your present system[/COLOR]. It is risky to edit partitions and install new operating systems, so please backup the whole system (an image) or at least your personal files!

Then explain how you intend to install Ubuntu, and there will probably be several people helping you to find a good solution. I think that you should consider editing the drive with Gparted before starting the installation, and that you should make an [COLOR="red"]extended partition[/COLOR]. Inside that partition you can make one partition for the linux file system and one smaller swap partition.

---

### Post by skate2 on 2012-02-05
now i boot from usb
and this is a first installation pic:
[IMG]http://www.novinupload.com/uploads/13284676041.png[/IMG]

this is second pic:
[IMG]http://www.novinupload.com/uploads/13284676042.png[/IMG]

and this is third pic from gparted:
[IMG]http://www.novinupload.com/uploads/13284676053.png[/IMG]

---

### Post by sudodus on 2012-02-05
Hi again,

Don't start the installer yet! Only look at the drive with Gparted!

What about C: D: and G: Have you wiped them already or is there a problem, that Gparted cannot see them?

Have you backed up your system or at least your personal files?

And what do you want to do with your computer? Do you want to keep Windows and make a dual boot system or are you prepared to wipe windows? I suggest that you take your time and test several things running the live system: graphics, communications, some favourite type of activity: music, video, photo editing, making presentations ...

---

### Post by skate2 on 2012-02-05
thx dude
idont remove C: D: and G.
i can see from windows, and ubuntu live filemanager, and i access theme from ubuntu live, but in gparted cant see them. (in picture3 on my last post)
i backup my peronal data
and i want have a dual os, my win7 and ubuntu.

---

### Post by darkod on 2012-02-05
Are you using a gpt or msdos partition table?

In your first image you have two separate logical partitions. Usually all logical partitions are grouped into one extended partition. You can't have more than one extended partitions.

This might be the error making linux not see the partitions correctly, but sotimes windows ignores errors in the partitions.

If you don't have any data in your partition #1, the ext3 logical partition, try deleting it so that you don't have two separate logical partitions.

One more question: Have you ever used the hdd in raid? You might have meta data left over which windows ignores but linux doesn't.

---

### Post by ajgreeny on 2012-02-05
From the live ubuntu system, open a terminal and run ```
sudo fdisk -l
``` and then ```
sudo parted -l
```and report the output back here.

Both commands use a lower case L at the end, not 1.

---

