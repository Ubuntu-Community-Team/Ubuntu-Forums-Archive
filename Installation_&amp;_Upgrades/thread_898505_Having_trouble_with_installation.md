---
title: "Having trouble with installation"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by pedro3005 on 2008-08-23
I am a beginner in linux, and right now im using the live CD, so it proves that i burned my cd correctly. I tried to install and it went ok until it started talking about partitions and stuff, i let it the way it was chosen and hit ok it said Too Small Size or something like that. It's impossible because i got more than 160gb of free space, and 100 in a single partition. Anyone can help me solve this? thanks :)

---

### Post by Kevbert on 2008-08-23
Welcome to Ubuntu.
If you have already set up a partition for Ubuntu/Linux you need to delete it as the installer is probably trying to install in the free space at the end of the disk. Do you have another operating system, on one partition you wish to keep ?  If the answer is yes then you need to delete the empty partition.  How big is your memory (RAM) ?  The swap partition should be twice the ram size. 
What you need to do is to select manual partitioning.  Delete the partition that is empty.  Now select a new swap partition and make it twice the memory size.  Then create a new partition with the remaining empty space formatted ext3 with a mount point of /  Your install should be OK after that.
If you have any questions please ask.

---

### Post by pedro3005 on 2008-08-23
yes i have windows xp installed on C: and i would not like that deleted, i also have another partition with data, also cannot be deleted, leaving me with two partitions, one with almost 32gb and another with 128gb....
those are both empty, should i delete them? and if yes, how to? sorry, but im kinda noob at linux :)

---

### Post by coffeecat on 2008-08-23
> **pedro3005 said:**
> leaving me with two partitions, one with almost 32gb and another with 128gb....
those are both empty, should i delete them? and if yes, how to? sorry, but im kinda noob at linux :)

If you want to delete these, boot into the live CD and go to System > Applications > Partition Editor. That's Gparted, a really user-friendly GUI partitioning tool. You can delete the unwanted partitions there.

If you are unsure of anything, and if you can get internet connectivity from the live environment, you can take a screenshot of the Gparted window with Alt+PrintScreen and upload it to your post.

---

### Post by pedro3005 on 2008-08-23
i managed to open it and i think i found wich of the hard drives (i've got two) is it, but it does not let me delete anything.

in 1shd.png you'll find the hd i want to install and in 2nhd.png you'll find the one NO changes can be made.

help, anyone?

---

### Post by sandysandy on 2008-08-23
ur free space is just 7.84 mb on each of ur hdd so obviously u cannot install an OS into that.

u need to resize sdb5 or sda 5 (shrink) and make ubuntu partitions in free space (ext3) and SWAP.

---

### Post by pedro3005 on 2008-08-23
no kiddin' huh lol
you dont understand, those partitions are free and i wanna install in them... can't i do that? it makes me wish get my windows xp cd and delete the partitions from their partition manager........ :(

---

### Post by sandysandy on 2008-08-23
for creating new partitions or for resizing existing partitions u can use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by coffeecat on 2008-08-23
> **pedro3005 said:**
> i managed to open it and i think i found wich of the hard drives (i've got two) is it, but it does not let me delete anything.

You've got lock icons against all the partitions of both drives which means they are mounted. You can't delete mounted partitions. Did you click on any icons in Places > Computer to mount any of the partitions? Because I didn't think the live CD would mount anything without you asking.

Anyway, right-click on the partition(s) you want to delete and choose unmount. Then you'll be able to delete.

By the way, if you want to delete sdb5 and sdb2, delete sdb5 first, because sdb2 is the extended partition 'containing' the logical partition sdb5. But if you do, you'll have about 120GB unallocated space, and the installer will probably set you up with a 1-2GB swap partition and a just under 120GB root partition - which is **huge**. If you want something smaller, post back and someone will advise.

---

### Post by coffeecat on 2008-08-23
> **sandysandy said:**
> for creating new partitions or for resizing existing partitions u can use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)


Why do people keep recommending the Gparted live CD when there's a perfectly good Gparted on the Ubuntu CD? :evil: It's one of the big mysteries of life that I have never been able to fathom.

---

### Post by pedro3005 on 2008-08-23
tried to unmount and

Error org.freedesktop.Hal.Device.InterfaceLocked.

help?

---

### Post by coffeecat on 2008-08-23
> **pedro3005 said:**
> Error org.freedesktop.Hal.Device.InterfaceLocked.

Heaven only knows. :cry: I've never seen that before and google comes up with nothing. I have only one other suggestion to make for deleting those partitions. You have Windows on that machine, right? Have a look at my post (#5) in [this thread](http://ubuntuforums.org/showthread.php?t=897616). I describe how to delete partitions using Windows (I hope. :()

---

### Post by pedro3005 on 2008-08-23
I did it! I INSTALLED LINUX BITCHES! sorry about that, just needed to get it out of my system :)
Anyway, linux is working perfect, haven't tested windows yet, but i know that none of my files were erased. Just one thing though, i couldn't install my video card driver. It says not found. I've got a Nvidia Geforce 8800 512mb, anyone can help me with that? :)
thanks for the help everyone :D !!!

---

### Post by coffeecat on 2008-08-23
> **pedro3005 said:**
> Just one thing though, i couldn't install my video card driver. It says not found. I've got a Nvidia Geforce 8800 512mb

Was that from System > Administration > Hardware Drivers? That usually works OK. If you haven't found that yet, give it a go. Or - some people prefer Envy. That's a package you can install in System > Administration > Synaptic Package Manager, and it deals with downloading and installing proprietary drivers for nVidia and ATI cards. I'm not sure which package it is, but envyng-gtk might be the one - I've never bothered to use it as the first works for me. You could search the forum with 'Envy' for more details.

---

### Post by pedro3005 on 2008-08-23
thats OK i've managed to make it work..
just like if i download a application from the internet how do i install it?
i've downloaded the flash player and it's in .tar.gz , i installed it by the package installer thing, but it's good to know how to, because i know someday i'll need it, won't i? :)

---

