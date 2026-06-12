---
title: "Automating partitions during install"
date: 2020-06-19
forum: Installation &amp; Upgrades
---

### Post by EuclideanCoffee on 2020-06-19
This is for version 18.04 LTS, desktop.

With d-installer, you can create recipes and build different partition tables quickly.

I'm trying to build multiple mount locations automatically, but the challenge seems to be that the d-installer solution I use is unreliable. For some hardware, it works. Other hardware it fails. Now there may be a subtle difference between hardware drives, but I'd like a more reliable option.

Do you know of a way to better automate building partition tables, or is there a known preseed that works (that I can't find because I've tried so many from wiki)?

The partition tables should also be lvm and support encryption.

Thank you.

---

### Post by sudodus on 2020-06-19
Have you got any idea of why the debian installer fails in some cases? And in such cases, should we expect that other methods would work better?

How many partition tables are you planning to make with this automatic method?

How flexible do you want it? For example,

1. You can clone a master partition table, if all drives have the same size, or it is OK that the smallest drive decides how much drive size that is used.

2. It is more flexible with a shellscript using fdisk or parted to create the partitions before you start the installer. It might be easier to make a shellscript for one particular task. I use such a method to create partitions in mkusb, when it creates a persistent live drive (in the shellscript dus-persistent).

Edit: In case 2 you must also use command line tools to create LVM and LUKS encryption. I have no experience of doing that manually, but I am sure you can find enough knowledge about it, maybe from Paddy Landau, who manages a [tutorial thread](https://ubuntuforums.org/showthread.php?t=2399092) about it.

---

### Post by EuclideanCoffee on 2020-06-19
At least 5 tables, if I parse your question correctly.

In my earlier builds, I was happy to have my partition tables prioritize space for /home and / with /var and /tmp being smaller.

I would like to learn how you implement shell script with d-installer, so I can simply have it run at boot-up.

---

### Post by sudodus on 2020-06-20
With 5 partition tables might be feasible to have templates (saved as compressed image files and easy to expand to the target drives).

My idea with a template or shellscript is to use it before the installer is started (and to use 'manual partitioning' in order to use the partition table available).

By the way, is it important to have separate partitions for home, var and tmp? Why not have everything in the root partition. if they are in the same drive?

---

### Post by EuclideanCoffee on 2020-06-20
It is absolutely essential to have everything separated.

I can already accomplish everything with automation besides separating the partitions and encrypting them.

Today I automate EFI builds without separating the partitions. Encryption works too.

---

### Post by dragonfly41 on 2020-06-22
Whenever I suggest webmin in a thread there is a chorus of "oh not webmin". But it has a bunch of useful tools which on occasion I use.
Although I have never tried LVM, since you mention it there is [this documentation]("https://doxfer.webmin.com/Webmin/Logical_Volume_Management").
For automation I could envisage adding an automation script to navigate the webmin GUI.

[https://doxfer.webmin.com/mediawiki/images/1/18/LVM_Logical_Volumes.png](https://doxfer.webmin.com/mediawiki/images/1/18/LVM_Logical_Volumes.png)

---

### Post by EuclideanCoffee on 2020-06-22
That's an interesting proposal, webmin.

I think it would work for a different project. I wouldn't go this route for this project, as relying on API is sticky. I want to be able to this entirely offline.

---

### Post by oldfred on 2020-06-22
I do not normally do server installs, but saw this:

[https://discourse.ubuntu.com/t/automated-server-installs/16612](https://discourse.ubuntu.com/t/automated-server-installs/16612)
> The server installer for 20.04 supports a new mode of operation:  automated installation, autoinstallation for short. You might also know  this feature as unattended or handsoff or preseeded installation.



---

### Post by EuclideanCoffee on 2020-06-22
Thanks for the pointer, oldfred.

It's on my todo list to support 20.04 LTS. I really, really hope this means there is better support in 20.04 LTS for this sort of task.

---

