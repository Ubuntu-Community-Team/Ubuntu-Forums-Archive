---
title: "Raid 0"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by AmJaD on 2008-04-07
With the new Ubuntu Hardy Heron (8.04) coming up the main issue some noobs have is installing Linux on a raid setup.

Most of my friends and I use windows with a Raid0 setup (its really easy with the windows version) and then use virtual box or some other virtual PC to install windows on.

What we want to know is with the this latest version of Ubuntu will it have the driver already installed without the fatal Grub error that comes at 94% (which is another thing... why 94%, why not 12% or before it downloads the updates during installation :P).

Back to the main issue, having Hardy Heron identifying that you have a raid setup (or at least something like the windows way of installing OS's on raid) would be awesome. we really don't want to go through that whole dmraid  and partition setup thing, just a headache for us noobs.

---

### Post by InTheFlow on 2008-04-07
Funny how you asked this question as I was coming here to search for the answer myself. I tried the beta version and it doesn't seem to show RAID drives during the install.  From what you said above, it sounds like installing Ubuntu on a RAID array is an exercise in frustration. :(

---

### Post by |2A|N on 2008-04-07
I would also like to see support for this in Hardy as well.  :KS

---

### Post by Re@p3rM4n on 2008-04-07
my computer has RAID-0 and i want to install ubuntu on it. is there ANY way to do this? -R

---

### Post by AmJaD on 2008-04-07
from what i read you can do it...

when i was researching it i came across 2 really helpfully sites from this guy called |flash| but they where both a nightmare to follow

the first link (this is the one that makes you cry):
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

the second link (this is the one that gives you a heart attack):
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

you have to follow the whole thing step-by-step and after a while it does become VERY dauntingly since you gave to wait for it to download and the program.
make sure you get also install the grub part of the installation very carefully or you get the fatal error at 94%.

from what i remember is that other Linux distros have raid 0 support. hopefully they will integrate it within the Ubuntu 8 series onwards.

---

### Post by Re@p3rM4n on 2008-04-07
Is there a way to do it on another version of Ubuntu or another distro without crying  or having a heart attack?
-R

---

### Post by dstew on 2008-04-07
It is very easy to install Ubuntu on a RAID0, or RAID1, or RAID5 array. The Alternate Install CD can set up these RAIDs prior to installation, or detect RAID arrays that are already there. You get the Alternate Install CD from the Ubuntu Download page, just check the box below the Start Download button.

You set up the RAID by assigning partitions to "Physical Volume for RAID" in the Use As line (the first line) in the partitioner setup. When you have assigned the partitions to be used, then you go to Configure RAID at the top of the partitioner main menu, as I recall. There, you create the devices, and then you can create the partitions on them.

Having said this, you can only ***boot*** a RAID1 device. This is because the LILO and grub boot loaders do not have the ability to get their configuration files from a striped RAID, only from a mirrored RAID. What I did recently, was create a RAID5 array for my root partition, and created a small RAID1 array (100 Mb partitions) for a /boot partition. At the end of the installation, I installed grub as usual, and it was able to get its menu from the (hd0,0) partition of the RAID1 because it is mirrored, and grub doesn't know that it is part of a RAID. Installing grub or LILO on the RAID5 failed though (I tried).

---

### Post by Re@p3rM4n on 2008-04-07
akay, i have a alienware laptop. it has only two drives raid-0ed together. how can i install linux on it. keep in mind that since its a laptop i cant add any drives or other components.
-R

---

### Post by dstew on 2008-04-07
You can install Ubuntu to a RAID-0 device, but you won't be able to boot it, so I don't think you should bother trying. What OS do you have on it at present? If that OS has a multi-boot loader, maybe you can configure it to boot an Ubuntu system on the RAID-0.

But why bother with RAID-0? It is not really redundant, that is, if you lose a disk, you lose everything. Maybe it has a speed advantage over individual disks, but I don't know...

---

### Post by AmJaD on 2008-04-07
well if you say it like that then there really is no point of downloading the alternative CD. i would have successfully installed Ubuntu on a raid 0 and then it wont even load up:P.
Its kinda sounds like a CUI way of getting the grub error:)...lol

---

### Post by Re@p3rM4n on 2008-04-08
assume you were in my position. i want to install linux on my laptop. i cant change my hardware config. what should i do? this is a serious question.
-R

---

### Post by AmJaD on 2008-04-08
Well you say that you got an alienware laptop so im assuming that its pretty powerful. It also says that you want to install Linux on ur laptop (didn't say Ubuntu specifically). for this i can recommend 2 options. 

1stly: once you set up a raid array on your computer/laptop get a Linux distro that does support raid0, there are some out there, im pretty sure of that.

2ndly: Use a VM to install Ubuntu on you existing OS (this is what i did and its awesome). especially if your new to the Linux worlds and want to learn about it before making the WHOLE switch. there will be some limitations that im trying to get around (posted one of them below if you want to read) but they are really minor and by the time you get up and running and comfortable with Ubuntu they hopefully would have some raid array support

[http://ubuntuforums.org/showthread.php?p=4675549#post4675549](http://ubuntuforums.org/showthread.php?p=4675549#post4675549)

a couple of known virtual machines are Msoft Virtual PC, Vmware  but the one that i use is VirtualBox
link below are:

VirtualBox Home page:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

if you need help on how to set it all up ill post a youtube video

anyway, hope that helps:)

---

### Post by Siyfion on 2008-04-08
> **dstew said:**
> You can install Ubuntu to a RAID-0 device, but you won't be able to boot it, so I don't think you should bother trying. What OS do you have on it at present? If that OS has a multi-boot loader, maybe you can configure it to boot an Ubuntu system on the RAID-0.

But why bother with RAID-0? It is not really redundant, that is, if you lose a disk, you lose everything. Maybe it has a speed advantage over individual disks, but I don't know...

Utter nonsense! Of course you can boot from a RAID 0 drive, I have 4 drives set up in two individual RAID 0 drives, and I installed Ubuntu and booted from it fine.

You have to do it the annoying dmraid -> fdisk -> manual grub install, route.. But it IS do-able.

I for one would love to see a Fedora-level of ease of RAID installations added to Hardy Heron.

P.S. And as for why, you got it in one, true hardware RAID 0 can be nearly twice as fast as a single drive in sequencial reads and writes..

---

### Post by dstew on 2008-04-08
> Utter nonsense! Of course you can boot from a RAID 0 driveHow did you do this? I would like to boot a RAID-5, if it is really possible. Can you refer me to the method you used? What is the dmraid-> fdisk -> manual grub install route?

EDIT: I am educating myself. Seems I was using software RAID, and for that it is true, you cannot install grub to a soft-raid 0 or 5, but only to a soft-raid 1. However, there is a kind of hybrid hardware-software RAID called "fakeraid" that looks like what you are talking about. The [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto") is about that kind of RAID, not about softraid. Am I right? So, it is possible to install grub to a striped RAID, as long as it is pure hardware RAID, or fakeraid. But you cannot install grub to a striped softraid.

---

