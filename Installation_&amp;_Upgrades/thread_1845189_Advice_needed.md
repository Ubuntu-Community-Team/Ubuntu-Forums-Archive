---
title: "Advice needed"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by Donalt2010 on 2011-09-16
I am currently running Ubuntu 10.04 32 bit on my laptop, which when new had Windows 7 installed, I completely removed Windows and installed Ubuntu. That was over a year ago now. My machine can run 64 bit operating systems, so what I have decided to do is start fresh with Ubuntu 64 bit and Windows 7. I am currently backing up all my important data to a Seagate 500 gb usb hard drive which is brand new. I guess what I want to know is which operating system should be installed first, and what steps should I take before I proceed to wipe everything.

---

### Post by drs305 on 2011-09-16
I would install W7 first. When you install Ubuntu Grub 2 will take over booting and should offer Windows as one of the menu choices. If it doesn't, it's an easy fix. 

Next, if you are not going to use your existing partitions, I would repartition/resize the partitions from within Windows just to keep it happy. 

Finally I would install Ubuntu, using the manual partitioning option so you can choose the partition on which to install Ubuntu.

If you have a lot of customizations you'd like to keep, you could move /home to a separate partition before your reinstall. In that case, you would designate the /home partition while installing Ubuntu and make sure you leave the 'format partition' option unticked.

---

### Post by e79 on 2011-09-16
As long as you backed up all your important file, here is how you should proceed imho.

1. Zero-out your drive with something like DBAN or KILLDISK.
2. Install Windows 7  first
3. Then Ubuntu 11.04

Should be that simple :p

---

### Post by Blasphemist on 2011-09-16
I agree with everything above and will add this. My win 7 install existed before I installed ubuntu. I installed ubuntu without manually partitioning or pre-install prep of the hdd. So ubuntu's install shrunk the windows partiton to create free space. It didn't shrink it enough, left way to much of the drive to windows. I say that because I came to use ubuntu as my main os and most of the free space was on the windows partition.

This is a bit of a long way of saying that if you manually do your partitioning after installing windows, you have much better control of how much space to give each OS. My experience was that windows disk management tools could not do a good job of shrinking the windows partition and that makes good sense to me as it is using the partition at the time. I prefer to do the partitioning using GParted from a live CD including the shrinking of the windows partition.

Personally, I've found that I enjoy the ability to try multiple versions of Ubuntu and other distros. Part of the beauty of Linux and FOSS in my opinion. I now have 7 distro partitions, windows, a swap and a ntfs formatted partition for sharing docs, pictures, downloads, etc. between anything I boot to. So I recommend you not waste a lot of free space for in the windows partition, create a shared part formatted ntfs larger than the amount of pictures, music, etc. you expect, 15-20GB linux OS parts at least though a clean install only uses less than 5GB and end with a swap a little larger than the most memory you will have. The only part that needs to be primary is windows.

---

### Post by Donalt2010 on 2011-09-16
> **e79 said:**
> As long as you backed up all your important file, here is how you should proceed imho.

1. Zero-out your drive with something like DBAN or KILLDISK.
2. Install Windows 7  first
3. Then Ubuntu 11.04

Should be that simple :p

What do you mean zero-out, completely wipe it first of then install the Operating systems?

---

### Post by e79 on 2011-09-16
Yes re-writing the whole drive with zeros (this erase everything, previous MBR and Grub included). I always consider it as a good step when reformatting/reinstalling. Its a bit like having a fresh new drive to install onto.

---

### Post by Donalt2010 on 2011-09-16
I'm not as technical as I thought about this subject of DBAN and KILLDISK, will I still be able to load the OSes after I run either of these programs?

---

### Post by e79 on 2011-09-18
Sorry for the late reply as I was away for the weekend.

To make it simple, Zeroing-out your drive means writing zeros all over it so you can be sure there is no residual information about previous OS or Boot Records and you can then do a safe clean install of any OS you want.

Download and burn a '[Ultimate Boot CD]("http://www.ultimatebootcd.com/")', you should find both tools under hard-drive/wiping section.

Cheers

---

