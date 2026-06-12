---
title: "dual-boot with vista"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by stunet on 2008-08-11
hello,

I am slightly new to linux.

I currently have my laptop dual-booted with vista & opensuse 11.0

however opensuse 11 is not running well with my laptop and 10.3 had an issue with the wireless connection.

i tried the kubuntu live CD which detected the wireless and plays well with my laptop :)

while trying to install kubuntu i had a hard time trying to remove opensuse(may just be me but it looks like kubuntu was going to keep opensuse which i do not want to do)

i tried to just remove the opensuse partitions but i do not know the linux partition system well enough so it was hard for me to figure out how to partition the system for kubuntu.

i hope someone can assist me in doing this as i rather like kubuntu(and opensuse, but need a better system for it though)

I have thought about going 100% linux on the laptop but currently not possible as this is used at uni and requires i have windows to do a few things.

much thanks :)

---

### Post by shr2004 on 2008-08-12
First of all, I am not an expert in linux. However I am using dual boot with Vista and Ubuntu hardy, and I have gone through several installation trials. From that I can share my experience which might help you to solve your problem.
You have live Kubuntu CD. While running live CD you can use gparted in the System>Administration>Partition Editor (or something similar in Kubuntu). It is a gui based partition editor. There are lot of how to out there, which you can search in this forum also in google to know about it. Its very simple to use. It will show you the available partitions in your machine and from there you can easily detect which is your Win partition. Keeping that intact you can delete the other partition. 
After deleting the partition you can install Kubuntu in that partition and it will handle everything upto dual boot menu.
Do a little search on dual boot in this forum after your installation to know about it better.

---

### Post by zchenyu on 2008-08-12
Kubuntu uses KDE, and does not come with GParted (last time I checked). I think the partition editor for KDE is QParted or something along those lines.

The easiest way to tell a Windows partition from a Linux partition is the partition type. Windows uses ntfs, and in rare cases of older versions FAT32. Linux however uses different partition types, perhaps most notably EXT3.

Also, I'm curious as to why you need to keep Windows at all. Most software for Windows can run perfectly well on Linux via Wine, or if the occasion calls, a virtual machine. You will find that in many, if not most, cases, Linux alternatives work just as well as their Windows counter-part, if not better. ;)

---

### Post by stunet on 2008-08-12
> **zchenyu said:**
> Also, I'm curious as to why you need to keep Windows at all. Most software for Windows can run perfectly well on Linux via Wine, or if the occasion calls, a virtual machine. You will find that in many, if not most, cases, Linux alternatives work just as well as their Windows counter-part, if not better. ;)

actually its for school reasons really.

for a few things i do it requires vista and windows apps like access and VS.net 2005

i do plan to make it 100% kubuntu after im finished with school next spring.

i also need to learn the ropes of linux better hence the dual-boot ;)

I'll look for that partition item on the live CD and see where it leads me too

thanks for your help everyone :)

---

### Post by suryapraveen on 2008-08-12
you can try vmware and run multiple OS where the VMware will help you to partition each OS.

---

### Post by NoWayBill on 2008-08-12
The installer has it's own partitioner.
When it gets to that point select "Manual".
Then simply select the Linux partitions.
They can also be resized at this time if you found the sizes impractical with OpenSuSe.

I have found that 8gig for both / and /home work nicely.
I mount the remainder as /archive and use it to store backups, music and such.
Then, when I foul the Linux install by getting into stuff I don't fully understand, reinstalling isn't so painful.
Or switching distros, which I do alot, or if upgrading I always do a clean install.

---

### Post by stunet on 2008-08-12
well i know the installer has a partion setup, but i couldnt figure out the way linux works with the partition.

i tried it and i got a few errors, the previous idea will be worth trying.

i have thought about the vm idea and would be something to look into.

---

