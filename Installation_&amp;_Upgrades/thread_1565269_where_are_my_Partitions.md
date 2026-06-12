---
title: "where are my Partitions"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by norseman-has-a-laptop on 2010-08-31
ok im working on my buddies computer he is messing with ubuntu 10.04
well we go to install it and well there are no partitions on install or any at all for that matter.

he has two hard drives a quad core i5

and the wireless doesn't seem to want to work either (i think because of the partitions)
if you have any ideas to fix.
Norseman

---

### Post by pricetech on 2010-08-31
If it's installed, you have to have at least one partition.  Why is it you think you have no partitions ??

I'm deducing that it's installed because you're saying the wireless isn't working.

---

### Post by norseman-has-a-laptop on 2010-08-31
no i mean the partitions are not there we have not installed it yet
and on the laptop on the wireless was not working and i went to the partions nothing but the laptop os is running off a usb.
but the main comp is the one that is showing no partitions too and we are trying to install on the other hdd

---

### Post by srs5694 on 2010-08-31
Please be more precise. "Showing no partitions" doesn't tell us what software you're using to ascertain that condition. It could be based on (among many others):


[list]
[*]The output of the "ls /dev/sd??" command, typed at a command prompt
[*]The display in GParted
[*]The report of GNU Parted (the parted text-mode program)
[*]The report of fdisk
[*]The report of gdisk
[*]What's displayed in the partitioning stage of the installation
[/list]


Furthermore, a complete lack of any partitions is perfectly normal on a new disk. If you've got a disk with an existing installation of Windows, OS X, Linux, FreeBSD, or any other OS, you should see partitions on the disk, but not on a new disk.

All that said, my suspicion is that you're running into [this problem.](http://www.rodsbooks.com/missing-parts/index.html) The Web page provides a solution, but it's rather technical. (I know of no easy point-and-click solution to this specific problem.)

If you need more help, you'll have to post more information.

---

