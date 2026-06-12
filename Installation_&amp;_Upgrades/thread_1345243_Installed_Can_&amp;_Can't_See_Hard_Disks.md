---
title: "Installed Can &amp; Can't See Hard Disks"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by PeEllAvaj on 2009-12-03
I'm trying to do a fresh install of Ubuntu or Kubuntu (I have tried both disks) on a new machine that used to run Fedora. When I get into the installer, the step where the partitioning is done, it doesn't report any disks found and I can't move the install forward.  

This is really weird because gparted and dolphin both report seeing the disk.  I am even able to read/write to/from it, and edit the partition table just fine.

Any ideas?

---

### Post by phillw on 2009-12-03
> **PeEllAvaj said:**
> I'm trying to do a fresh install of Ubuntu or Kubuntu (I have tried both disks) on a new machine that used to run Fedora. When I get into the installer, the step where the partitioning is done, it doesn't report any disks found and I can't move the install forward.  

This is really weird because gparted and dolphin both report seeing the disk.  I am even able to read/write to/from it, and edit the partition table just fine.

Any ideas?
Hi

Set the area of the disk (possibly all of it - it doesn't matter) that you're going to use for Ubuntu to 'un-allocated'. i.e. - remove the file system completely from it. Then Ubuntu should give you the option to use unallocated space.
If it's going to be 100% Ubuntu - make sure that is only one partition - and it is unallocated

Phill

---

### Post by PeEllAvaj on 2009-12-03
I just tried deleting the partition, so that all 400GB of the Sata drive show up as "unallocated" in gparted.  I then restarted the installer, and it still doesn't show any drives after the keyboard step, and none of the buttons "add" "delete", etc do anything.

Any other ideas?

---

### Post by PeEllAvaj on 2009-12-04
Bump.  I'm pretty technical, is there anything I can do to debug ubiquity, to see from a technical perspective what is failing?  I tried running it from the command line and watching the output, but that didn't give me anything new regarding the problem.

---

### Post by pyromax on 2009-12-04
uhm, you might want to look into the raid controller ubuntu suddenly needs. I know it messed up my setup pretty good. 
Unfortunately, I kind of lost the thread which I used to get the most hints, sorry.

---

### Post by Furious87 on 2009-12-04
Im having this exact same problem, my sata controller is should be a Silicon Image 3112 SATA or a Silicon Image 3512 SATA. im not shure cuss both of thoose uses the same driver.

A thing ive noticed if i format the hdd and mount it. it shows up as it should on the desktop. BUT when i start the installer the hdd magically disappears. AND when i close the installer the hdd icon appears again.

my guess is that somthing is really off with the installer. im gonna try to dl a older version of ubuntu and see if i get the same problem. that is if someone doesnt figure this out :D

---

### Post by Furious87 on 2009-12-05
[http://img710.imageshack.us/img710/2249/screenshotk.png]("http://img710.imageshack.us/img710/2249/screenshotk.png")

there is a screen shot of my installer. and a screenshot of Gparted, Disk Utility and A Terminal with "sudo fdisk -l"

Someone on irc said something about AHCI. but i cant figure out what that is and how i enable/disable it in my bios.

---

### Post by raymondh on 2009-12-05
I've seen a thread where dmraid was removed.  In liveCD and in live session, access a terminal and type

```
sudp apt-get remove dmraid
```

Then exit terminal, exit live session and try to install.

Another tip (from presence1960) is in step 4 of the installer and select the proper HD in the top right corner.

Hope that helps.

---

### Post by Furious87 on 2009-12-05
removing dmraid is works for me.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054)

---

### Post by PeEllAvaj on 2009-12-05
Removing dmraid with "sudo apt-get remove dmraid" worked for me!

Thank you so much everyone!

---

### Post by raymondh on 2009-12-05
glad it worked ...

happy ubuntu-ing :)

---

