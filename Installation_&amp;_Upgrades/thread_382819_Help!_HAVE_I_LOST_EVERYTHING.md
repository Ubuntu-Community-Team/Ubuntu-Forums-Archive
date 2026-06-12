---
title: "Help! HAVE I LOST EVERYTHING?"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by mswnow on 2007-03-12
So, before you call me stupid, sympathize with me. I have about 6000 pictures on my computer. I care about every one of them. I have a dell inspiron e1705. I have an external 250 GB LACIE HDD. I was trying to instal kubuntu to a partition on the external drive. When I tried to boot to it it said missing OS. 

I re-installed it. I made the root and swap partitions on the external drive. in the menu listing mounted drives, It listed the partitions on my main drive as media/sda1, etc. then it listed the other partitions as "/" and swap

the computer lost power half way through the instalation. When I tried to boot XP, it said missing OS, when I select boot from first HD in the kubuntu installer, it says: 
Booting from local disk...
GRUB loading stage 1.5.


GRUB loading, please wait...
error 15





WHAT DOES THIS MEAN? HELP!!!!! 

Please dont tell me I have lost everything! it is very important I get these files back!!!

---

### Post by finer recliner on 2007-03-12
throw the live disk back in (your ubuntu install disk) and poke around your drives using that. see what you can find, and BACK IT UP! then try to reinstall.

---

### Post by mswnow on 2007-03-12
What do you mean, poke arround in my drives? and how do I back it up if i cant boot XP? I cant remove the drive from the computer because I have no shell for it. please elaborate. 

Is my data gone? how do i fix this? if I reinstall it with the live CD will that bring XP back to life? 

please explain these things to me. I am in serious trouble if I cannot restore XP to working condition!

---

### Post by codejunkie on 2007-03-12
it doesn't seem like you've lost anything yet, **but do not reinstall anything right now**. what the problem is you installed ubuntu onto the usb drive, and grub installed it's self to the mbr of your windows drive, not the usb drive. here's the problem grub needs to read the menu'lst file that's stored on the usb drive and it can't find it so it can't load the boot menu.

try this to recover your winows install, insert your windows xp cd, boot with it in the drive like your going to install windows, do not choose install choose the **recovery console** option this will boot into a command prompt, now choose the windows install usually just hit 1 then enter if you only have one version on windows installed, it will ask for a password give the administrator password if you have set one if not just hit enter type ```
fixmbr
``` remove the cd and reboot the computer and it should take you into windows.

---

### Post by finer recliner on 2007-03-12
your data is probably intact. here's how to get at it when you cannot boot any operating systems successfully:

put your ubuntu install disk into the CD tray and boot from it. this will make it act as a live disk (running ubuntu from memory without actaully installing it). now you can mount your other drives/partitions and browse them as usual. find your pictures and back them up on a thumb drive or burn them to a blank CD (if you have one CD tray, this may not work since ubuntu is using your cd tray at the moment).

---

### Post by mswnow on 2007-03-12
So how do I fix this? can you please help? Thank you so much for trying to help!

---

### Post by mswnow on 2007-03-12
Thank you! I dont understand though, can kubuntu read a NTFS file system? and I have 6000 pictures throughout the drive, can I back-up the entire drive? How do I do this? 

also, how do I fix the problem of GRUB looking for the file on the USB drive?

---

### Post by JamieC on 2007-03-12
First of all, boot the live disc as already suggested. Open a new terminal window (Applications -> Accessories -> Terminal) and paste the output of the following command:
```

sudo fdisk -l | grep NTFS

```

This will allow us to determine which device your files are on, we can then help you mount it and attempt to retrieve the files. This is the most important thing for now.

---

### Post by finer recliner on 2007-03-12
kubuntu can read NTFS with no problem. 
how to mount drives: 
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
or 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

if you boot your live disk without the USB drive plugged in, wait to fully boot. then plug in your USB drive, ubuntu should automatically find it and mount it for you.


i'm not sure how to fix GRUB.

---

### Post by finer recliner on 2007-03-12
to back up files, all you need to do is simply find the files you want with a file browser (in kubuntu, use konquerer) and then copy them to a new location that is not on the same physcial drive (i.e. a thumb drive or CD-R)

---

### Post by mswnow on 2007-03-12
okay. I think I did that right jamie C here is what it gave me:

/dev/sda2 *          7         13725        110197867+    7  HPFS/ NTFS
/dev/sdb2       15201       27948         102398310      7   HPFS/NTFS

---

### Post by mswnow on 2007-03-12
can you please help me?

---

### Post by konungursvia on 2007-03-12
Using your install CD, you can boot from it into Linux, without touching the hard disks, and without installing anything. Then you can still open your nautilus or file browsers, and look at the actual files you have on the all the disks. You can then see if you have all the photos, and before doing anything else, copy them to another drive.

---

### Post by mswnow on 2007-03-12
I have mounted the drive to /mnt as one of the guides told me, but how do I get to it after that. can someone help?

---

### Post by finer recliner on 2007-03-12
open your file browser and type /mnt in the address bar. that should put you in the drive so you can view all your files. now go find your pictures

---

