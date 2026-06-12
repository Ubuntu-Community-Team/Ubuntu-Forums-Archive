---
title: "Ubuntu does not boot."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by chethanshenava on 2010-01-15
[COLOR=Black]Hi,

I have Windows XP installed in C drive 30GB. I used my 30GB D drive to install Ubuntu 9.10. I followed the steps from [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml) . For Hard disk partitioning, I used "Specify partitions manually". The instalation was sucessful. But when start my computer, it always goes to Windows XP and does not give me any option to choose the OS i want to use

Please help.

Thanks!
Chethan Shenava
[/COLOR]

---

### Post by audiomick on 2010-01-15
Hallo.
Your grub is messed up.
Read this
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
for info on how to sort it out.

---

### Post by Leppie on 2010-01-15
where did you install grub?
also, is the "d" drive a real drive or a partition?

---

### Post by chethanshenava on 2010-01-16
The D drive is a partition. And i believe the grub is installed automatically to the /.

---

### Post by kansasnoob on 2010-01-16
It would be very helpful if you'd boot the Live CD and then post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by chethanshenava on 2010-01-16
Okay, I will paste the results here soon. However, I have a question. Should ubuntu be installed in the drive which is not beyond the 1024 cylinder boundary? Most of the old OS in Windows does not boot the OS if it is installed beyond the 1024 cylinder boundary. As mentioned i have installed ubuntu and i think it is beyond the cylinder boundary.

---

### Post by Leppie on 2010-01-16
this depends more on the bios of your machine. most bios's now support booting past cylinder 1024, but if your machine has an old bios it may not work. though you can circumvent this by creating a boot partition in a lower region.

---

### Post by chethanshenava on 2010-01-18
The issue is resolved :D. I think it was an issue with the partition. I then installed Ubuntu in the first drive of an extended partition. That resolved the issue. 

Now I have a new problem. Not a problem actually. I installed the updates and a new version of the grub was installed. However, the older one is not removed. When the machine boots, along with the Windows OS, i get two other option those are:

1. Ubuntu, Linux 2.6.31-17-generic
2. Ubuntu, Linux 2.6.31-14-generic

I think Ubuntu, Linux 2.6.31-14-generic is a older one.

Is there any way to remove this? Because i think, whenever there is an upgrade it is going to keep the old information. 

How can this be done?:(

---

### Post by Leppie on 2010-01-18
you do not have 2 versions of grub. you received a kernel update. i've been running the 17 kernel since it came through and never had any issues with it. i would suggest you try it for a while and if it is stable on your machine, you can remove the 14 kernel by going into synaptic (System>Administration>Synaptic Package Manager) and type "linux-" (without the quotes) in the quick search box. select the 14 kernel packages and mark for removal, then click the apply button. this will also remove the menu entry for this kernel version.

---

### Post by Cheezespread on 2010-01-18
Yes , you can remove them using Synaptic as described. But I would suggest you to keep them since 14 seems to be the adjacent kernel version which you have. If at all 17 breaks on you , you would have something to go back to fix the issue.

Or if you are just annoyed by too many entries in the menu , you could just hash them out in the menu list file .

---

### Post by chethanshenava on 2010-01-18
Thank you guys! Thanks for the help. This is the first time I am using Ubuntu and I am sure i will enjoy this.:D

---

### Post by Leppie on 2010-01-19
i'm glad your system is working as you want it to now.
ubuntu is a very nice distro, i'm sure you'll like it.
and with all the help offered on this forum, you're most likely to find a solution quickly :)
welcome to the world of open source ;)

---

