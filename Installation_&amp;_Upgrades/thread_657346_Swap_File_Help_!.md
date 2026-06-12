---
title: "Swap File Help !"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Niggy on 2008-01-03
Hi all.

Just a quick intro to my issue so you know what has happened so far.

Decided to try Linux the other day and promptly went for Ubuntu after reading various articles. I downloaded and ran the CD from boot to try it before I installed. All was looking well so decided was time to install so I could try things that were not possible without installing and also it running slow via DVD rom.

Ok, I have various hard drives Sata and IDE. I have always kept my C:/ Drive as an OS drive only and never store data or anything on it, that way if I crash n burn with wonderful Windows XP I can format and be up and running fast with not much loss as all data is saved on other drives. So I decided the best thing to do is create a partition on this drive to install Ubuntu, I fired up Partition Magic and created a Ext partition for the installation as that is what I had read on another forum as a good step to take before starting the install process.

I then booted Ubuntu from the CD and proceeded with the install, this is where it went horribly wrong as it asked for a root drive ( I chose the new partition I had created ) and then it asked for a swap location - I selected one of my other drives ( G:/ Drive ) and pressed next, however the drive did have some data on that I wanted to keep but assumed the swap was just to create a swap file area ( Like windows ). The installation then stalled and failed for some reason. So I rebooted back to windows but after reboot my drive I had for swap my G:/ Drive had disappeared from windows drive list. I stated Partition Magic and there in glorious OH NOOOOO moment was my G:/ Drive showing as a Linux Swap drive and and empty one at that.

My question is a simple one after the long explanation... Can I recover my data ?????????? Help please I need the data on that drive I holds some work and files and pictures of one my kids in special care unit I don't want to loose. HELP

Again sorry for the long explanation but I wanted to cover as many questions you may have in resolving this issue. And sorry if this is in the wrong part of the forum but my head is spinning ....

---

### Post by Pumalite on 2008-01-03
Boot your Live CD and from terminal, run
sudo fdisk -lu
Identify G
In Terminal:
sudo mkdir /medis/sd? (what is G)
sudo mount -t ext3 /dev/sd? /media/sd?
Now take a look at your drive.

---

### Post by Niggy on 2008-01-03
OK now rebooted and have terminal open..

I have done the sudo fdisk -lu and have a list of drives etc infront of me...

In Terminal:
sudo mkdir /medis/sd? (what is G)   [COLOR="Blue"]Am I to replace /sd? with something ? [/COLOR]

Sorry but I am totally new to Linux and under death threats from the misses for losing these pics if I dont sort it.... :(

I read before you posted from another forum ( yes I should have waited for a reply to my post here ) that said change the swap back to ntfs in Partiton magic and it should reappear.. it didnt.. I fear now all is lost and I'm sleeping in the shed tonight ! 


Here is a copy paste for the drive thats shot ...  from the fdisk -lu command

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
16 heads, 63 sectors/track, 159560 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d264bd9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1            1008   160836479    80417736    f  W95 Ext'd (LBA)
/dev/hdd5            1071   160836479    80417704+   7  HPFS/NTFS

Hope this can help me

---

### Post by Pumalite on 2008-01-03
Make one for hdd1 and another for hdd5:
sudo mkdir /media/hdd5
sudo mount -t ntfs dev/hdd5 /media/hdd5
Navigate to that folder and take a look.
We'll deal with the other one later.
Tell me what you find.

---

