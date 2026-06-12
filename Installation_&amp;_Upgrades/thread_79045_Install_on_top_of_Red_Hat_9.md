---
title: "Install on top of Red Hat 9"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by inerte on 2005-10-19
Yeah, I am still using RH 9 :)

A co-worker installed Ubuntu on his machine, and I decided to also do it on my PC. I have experience installing Linux on top of Windows, the defrag and partitioning process, etc.

I don't need to dual-boot to RH 9, but I would like to keep my data on a different partition, and access it using Ubuntu. Another co-worker mentioned that a live-cd Linux distribution called Kurumin (which is based on Knoppix), has a graphical interface for parted, and using it I can resize my HD.

Can I use this parted, or does Ubuntu installation offers a way to keep my data on another partition? Or is there another, better way, to install Linux on top of Linux?

I will make backups of my HD, of course, but if I forget something... and since there's a variety of data everywhere, including source code, my popfile directory, Mysql databases, home directories when this machine was the office server... it's easier to have the whole HD available, if possible :)

Many thanks,

Julio Nobrega.

---

### Post by stuporglue on 2005-10-19
The absolute easiest way would be to get a second HD and install to that, then mount the RH9 HD somewhere so you can still access the data. 

I've never used it, but I think that the Ubuntu installer will let you resize your current Linux partition. If you're lucky, it will even add RH9 as a boot option in the grub menu. 

As always, resizing might lose data, backup first, blah blah blah.

---

### Post by pksings on 2005-10-19
You didn't state what partition(s) your data is on so my basic assumption is that you have /home on a separate partition than Redhat's "/" and "/boot". On my machine here /boot is /dev/hda2, / is /dev/hda3 and /home is /dev/hda6.

If so, good, you can replace Redhat with Ubuntu quite easily by using the manual partitioning leg and selecting whatever is your "/" partition and "/boot" partition and formating them, DO NOT format /home, you can select it to be mounted automatically but preserve the information in it.   You will have to know before you get to this what is what, so I suggest you cat /etc/fstab and maybe even print a copy before you whack Redhat.

If you do not have /home on a separate partition then you will probably have to resize a  partition and make one.   Partition Magic is definitely the easiest way to do this but costs $.  ( I already owned it so that is what I use )  I tried to use ntfs-resize but didn't do it properly and deleted the windows data accidentally. (Assuming you are going to keep Windows around, I have to for diagnostics on this Dell laptop). 

You probably, (read should) format / to get rid of all the Redhat libraries and files so they do not cause a problem with Ubuntu, I don't think it will let you install without doing it, but in case it does, it's not a good idea.  They are compiled with different versions of gcc, and are not strictly binary compatible so any leftover libraries could and probably will cause weird errors later. Better to start fresh.

Since all your data as a user is put in your "home" directory you can easily see the advantage of having that on a separate partition in case you ever want to change distros or suffer a major problem with the root (/) partition. You can then re-install without losing your personal data. Of course this doesn't protect from total drive failure but still it's wisdom is obvious.

Hope this helps

PK

---

