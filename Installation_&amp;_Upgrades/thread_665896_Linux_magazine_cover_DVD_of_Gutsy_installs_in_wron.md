---
title: "Linux magazine cover DVD of Gutsy installs in wrong place"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Dai84b on 2008-01-12
Hello 
It's my first week of Linux and Ubuntu. I created three partitions on a new 250gb HDD and copied over the Windows xp to the new system logical partition, the data to the second and reserved the third for linux. WD Lifeguard software was brilliant and it all went very well. 
I started with an installation of Edubuntu 7.04 using Wubi on the windows xp computer. It was very civilised and placed Edubuntu on the third HDD partition per my request and made a dual boot. I liked the results and changed to a LAN modem and was enjoying using ubuntu. 
I managed to wreck the system after downloading too may packages which turned out to be incomplete using the add/remove menu. 

Today I bought  Linux magazine solely for the cover mount DVD of Gutsy Gibbon thinking this will be a good way to replace what I had. I used WUBI to unistall Edubuntu 7.04. I rebooted the computer with the DVD in and it went straight into an installation without asking any questions.

I now have an installation of 7.10 on the C drive that I can't access. No dual boot. I can either go to xp [thankfully unharmed] or reinstall Gutsy from the DVD.  I think this is called vandalism. 

How do I uninstall the ubuntu I have in the wrong place?
Or how do I make it dual boot ?
How do I use the DVD to install to the partition I've already created in Windows ?

It's a super OS and software. When it goes in the correct place.  I've never come across a cover mount DVD that went straight into an install without asking where to go. 

Kind regards

David

---

### Post by rivalarrival on 2008-01-13
Linux is totally different from Windows. 

First off, "C drive" would be your windows partition, not the physical, 250gb hard disk. Linux usually refers to the first hard drive as "hda" and the first partition on the drive as "hda1"

Ubuntu generally uses at least two partitions, a "/" (or "root" partition) and a swap partition. The installer will create the partitions if you leave some space on the drive unpartitioned, or tell it which partitions it can modify.

Wubi is a completely different story. When you install ubuntu from wubi, it puts the entire ubuntu installation inside a file and "loop mounts" this file at boot. Wubi doesn't install to a partition.

Are you sure you're not mistaking the LiveCD for an installation?  The regular installation disk will boot from CD and bring up an ubuntu desktop.  It gives you a way to try out the operating system without changing anything on your hard drive.

---

### Post by zvacet on 2008-01-13
> How do I uninstall the ubuntu I have in the wrong place?
Or how do I make it dual boot ?
How do I use the DVD to install to the partition I've already created in Windows ?

Boot up your DVD and start with installation.when you come to the partition step choose manual and then you will see your partitions.Leave NTFS untouched and delete all ext3 partitions.That way you will get unallocated space to install Ubuntu.Beside root and swap it is good to have separate home partition.More details from all of this you can find [here](http://www.psychocats.net/ubuntu/).

---

### Post by Dai84b on 2008-01-13
Big thanks to rivalarrival and zvacet. 

This all exposes my ignorance and I've learnt a lot and met with success in the dual boot Gutsy Gibbon / xp  installation. 

I read all your instructions, those on the superb psychocats.net website and watched the screen cast by Alan Pope found under Google videos search *Ubuntu Dual boot*

During the install I did a manual partition on the 3rd volume of the drive that I mentioned, creating a swap file  area first, then a >10gb partition with the mount label   /   for root and, as  you suggested, gave the remainder of the partition to the mount designation /home

The remainder of the install went to plan. 
The only glitch is a minor one and the remains of having WUBI setup ubuntu. The windows boot screen after Wubi had deleted ubuntu left two choices,  both being Windows XP default [where one was Ubuntu previously] . The linux boot manager [with the name like Grump] has two windows boot entries. The obvious one labelled XP home edition goes to an error and the non-obvious Windows XP/NT/2000 loader goes to the Windows XP default twice boot screen mentioned above. It would be nice to fix this one day. Windows XP is fine. 

Ubuntu is looking good and I now know of a number of places to find well presented information for beginners. I shall read up on each alteration before executing it from now on!

Thanks very much

David

---

### Post by rivalarrival on 2008-01-13
Nothing wrong with a little ignorance - none of us know everything. The point of community support is to bring problems and solutions into the same room. 

Your minor glitch has a solution. You need to fix "grub" to remove the incorrect entries. This is potentially dangerous in that you may not be able to boot at all if you break it.

You'll also need to fix boot.ini on your windows partition to remove the wrong entries. Again, this is potentially dangerous in that you may not be able to boot to windows if you break it. 

If you do break them, you can recover with your windows and ubuntu installation disks. 

I don't have any experience fixing grub so I don't feel comfortable advising you on exactly how to do it. There are a number of how-to guides around, and a number of people more experienced in these problems. Your best bet is to search for them with Google, or start a new thread for this specific problem.

---

### Post by zvacet on 2008-01-14
It is good to know we have one more member.And now to the grub

```
sudo gedit /boot/grub/menu.lst
```

This command will edit your grub menu list and there you will find all boot entries.Put # sign in front of line of one you don´t want to show in your grub.Save and close the file.


```
sudo update grub
```

---

