---
title: "Windows install CD cannot find NTFS partition"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Radhavictory on 2011-05-03
Hello,

Ok so I'm running Ubuntu 11.04 on my Acer extensa 5620. I need to install windows and setup a dual boot on this machine. Here's what I did. I followed the instructions on this page 

([http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)) 

and resized my home partition (which is differenet from the file system partition). Anyways, I resized the partition and made a new NTFS partition. This was all done from Live CD. I then rebooted and then tried the windows installation CD. Now here my problem crops up.
Windows says that no partition is found. What have I done wrong? Any ideas? Can the drive be damaged or have I made a mistake some where? I did not specify a mount point for the new NTFS partition, does that matter?
Any tips or help would be greatly appreciated people, thanks!

---

### Post by dino99 on 2011-05-03
windows often disagree if its not installed on a primary partition at the  hdd beginning; so maybe you need to move your partitions a litle bit. And of course this ntfs partition need to be bootable.

what you need for ubuntu:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Radhavictory on 2011-05-03
> **dino99 said:**
> windows often disagree if its not installed on a primary partition at the  hdd beginning; so maybe you need to move your partitions a litle bit. And of course this ntfs partition need to be bootable.

what you need for ubuntu:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Thanks dino99. I'm still lost though. How do I move around the partitions? What do you mean by that? Also, how do I make it bootable? Will I have to do these things again with gparted from liveCD?

---

### Post by oldfred on 2011-05-03
The NTFS partition has to be a primary sda1 thru sda4 and has to have the boot flag (active partition in windows). Windows will only install, boot or repair a partition with the boot flag. 

Some BIOS will not even let you boot unless you have a boot flag on a primary partition. Grub does not use a boot flag.

---

### Post by srs5694 on 2011-05-03
If you're still mystified, Radhavictory, I suggest you post either the output of "sudo fdisk -lu" (between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings) or a screen shot of GParted showing your disk's partitions. That will give us the information we need to provide more specific recommendations.

---

### Post by Radhavictory on 2011-05-03
> **srs5694 said:**
> If you're still mystified, Radhavictory, I suggest you post either the output of "sudo fdisk -lu" (between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings) or a screen shot of GParted showing your disk's partitions. That will give us the information we need to provide more specific recommendations.

Thanks srs5694, you are right, I am still mystified. Here is a screenshot of my partitions shown by gparted.

[IMG]http://dl.dropbox.com/u/1212860/-dev-sda%20-%20GParted_002.png[/IMG]

---

