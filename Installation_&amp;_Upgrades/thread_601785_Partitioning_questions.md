---
title: "Partitioning questions"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Elman on 2007-11-03
Hi,

I've been using Wubi for a while to test Ubuntu and now, since I purchased an external usb HD recently I want to have install Ubuntu 7.10 in a partition (40Gb or something) in it, keeping the rest for sharing files between Windows and Ubuntu (In NTFS or Fat32, that doesn't matter since Ubuntu can write NTFS now, right?).

However, I'm a bit confused about the partitioning part of the installation (Using the Live CD). I've been looking for tutorials but I can't seem to figure it out yet, and I don't want to risk my Windows partition. Can anybody explain me how can I exactly make the desired partitions (A shared one for Windows and Ubuntu, and the rest for Ubuntu)? Is there any tutorial that explains it clearly, or something?

Also, would there be a noticeable performance decrease by using a usb external HD instead of an internal one (Not that I have a choice at the moment)?

Thanks :)

---

### Post by cuby on 2007-11-03
Hello, please see my this response in:

[http://ubuntuforums.org/showpost.php?p=3699327&postcount=2](http://ubuntuforums.org/showpost.php?p=3699327&postcount=2)

Bye and good luck.

---

### Post by Elman on 2007-11-03
Yeah, thanks. I already know what to do, I believe (I've found a few guides too), the problem is how to do it :P

Anyway, I have an internal HD with two 80GB partitions (One for Windows and programs, another for other files), and an external HD with a single 320GB partition.

[http://img530.imageshack.us/img530/1421/screenshotox2.png](http://img530.imageshack.us/img530/1421/screenshotox2.png)

So the Windows partitions are hda and hdb, and the external disk is sda.

Then, I just have to choose the first option, Guided - resize SCS|1 (0,0,0), partition #1 (sda) and use freed space, right? I know it seems pretty obvious, but I just want to be sure, I can't take any risks here.

Also, that % I have to select... Is it the new size of the current partition, or the size of the Ubuntu one? I mean, if I want 20% of the disk to be taken by Ubuntu (And 80% to be used for sharing files between Ubuntu and Windows), should I choose 20% or 80%?

Thanks :)

---

