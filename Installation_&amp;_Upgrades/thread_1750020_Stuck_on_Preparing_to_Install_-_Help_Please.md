---
title: "Stuck on Preparing to Install - Help Please"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by pearce007 on 2011-05-05
I got the same problem when I am trying to install Ubuntu:

I have tried running Ubuntu of the DVD and it works fine, but when it  comes to me installing Ubuntu I get past the select language page and to  the:

Preparing to install Ubuntu
For best results, please ensure that this computer:

(tick) has at least 4.4 GB available drive space
(tick) is plugged into a power source
(tick) is connected to the internet

I then press the 'Forward' button and thats as far as it gets, just the loading circle with no progress!

I have opened terminal and done the fdisk and these are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8357863

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1       59783   480201724   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           59783       60802     8182812   42  SFS
Partition 3 does not end on cylinder boundary.
ubuntu@ubuntu:~$ 

Does anyone know what I need to do next? :confused:

---

### Post by slanger87 on 2011-06-07
I'm stuck in the exact same place that you are. Did you just give up on it or end up figuring it out?

---

### Post by VanR on 2011-06-07
When it asked who are you? you didn't use a capital letter in your name did you? It doesn't like that. No capital letters allowed in your name. They should have a note about that on the install page.

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums pearce007 and slanger87 :-)

Here is the problem:
> 42  SFS

You have dynamic disks in Windows.

See this thread for more information:
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

Read the posts by oldfred and srs5694 carefully, they really know what they are talking about.

---

