---
title: "Very Big Installation Problem"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by d3sphil on 2006-12-14
Hello, first time here, and first time trying to install Linux actually.

So, I was running Windows XP on my desktop. Wanted to get a dual boot with Linux, more specifically Xubuntu, going. So, I downloaded the Live CD and tried it out. Liked it, so decided to get on and install the dang thing. So, I start the install process, and when I get to the partioning I selected to make a new one, and thought things were going okay, but then nothing happened. It just stuck there for a long time. So I decided to restart. Bad idea, to make a long story short, I wiped out the partion, and had to reinstall windows. That's not a problem. So, I get windows reinstalled quickly and want to try this again. So I boot it up, and start the install. I think things are going okay since the partioning part actually work and I get the the "INSTALL" button page. I click INSTALL and things start moving!!! But, unfortunatly the partion was not successful. Hm.. not sure what this means. I click continue, and the installer exits and I try it again. No luck. I restart, and suddenly nothing works. I mean, I am totaly screwed at this point. The system is not even finding my Hard Drive anymore?!!!! This could be really bad.

I need some help, I don't know what to do. I tried re-installing windows, but that just came up with a message that said it could not detect a hard drive. eh...... So I'm trying to install Xubuntu cleanly and see if it can somehow fix my hard drive issue. ANy suggestions/help to a newbie at this sort of thing?

Thanks =)

---

### Post by bernied on 2006-12-14
This might be a hardware problem - hard drives do fail. I've lost 3 in about 8 years. Does the live-cd still work ok?

---

### Post by d3sphil on 2006-12-14
Yeah, I have been messing around some more and it may very well be the hard drive that died. It just happened at a very coincidental time =). Anyway, I'm going to buy a new hard drive, and try again. I'm going to be away form my desktop for a month, but when I get back I'll let you know how this happens.

---

### Post by drphilngood on 2006-12-14
If it´s a Sata drive, you might want to make sure the cable is securely connected.  I´ve had similar problems and that´s been the problem most of the time.

---

### Post by Duck2006 on 2006-12-14
Use the CD that comes with the hard drive to partition the drive be for you setup any OS on it

---

### Post by wpshooter on 2006-12-14
Personally, I have serious doubts that there is anything physically wrong with your hard drive.

Why don't you go to the drive manufacturers website and download and run the diagnostic to check the integrity of the drive ?

My bet is that, you have to be fairly experienced to get this dual booting to work correctly and it is probably best attempted with the ALTERNATE CD of Ubuntu instead of the DESKTOP CD version.

After you test your drives integrity, and if you don't have anything on it to lose, why don't you download the **KILLDISK** program and** WIPE** the drive completely clean and give your installations another shot, first installing Windows and leaving yourself enough open space for your Ubuntu partitions and then come back with the ALTERNATE CD version of Xubuntu and attempt to install it.

[http://www.killdisk.com/](http://www.killdisk.com/)

Make sure you are also burning your Ubuntu CDs at 4X or less and that you are testing the integrity of your Ubuntu CDs by running the verification function found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by d3sphil on 2006-12-15
Update: I got my hard drive back up and running. Had to search around for my Hard Driver manufacturer's diagnostic (not so easy when you have a Dell). It said my hard drive was screwed, but a Low Level format (all 0s) on the partion space solved the problem. I'm installing windows right now.

---

### Post by bulldog on 2006-12-15
When your windows install is done,download the gparted live cd it's just 25MB and burn it to a disk.
Boot from it and follow the steps.
You end up with the partitions on your hard drive.
Now if you have used the whole disk for windows resize it [make it smaller] to create some space for ubuntu.
Make at least 10GB space for Ubuntu,but more is better :D 
Right click the free space and choose new partition and make a swap about 1GB.
Do the same again and create a new partition from the rest of the free space.
Format swap as swap and the other one as ext3.
Don't forget to hit the apply button,otherwise nothing will happen.
If done,exit the gparted cd and reboot with the ubuntu cd.

When coming to the partitioner,choose manual partitioning [already done that] and mount your swap as swap and the ext3 as / (root).
Hit the apply button after you have double checked your windows is **not** set to be formatted!!.
The install will continue but take the time for all steps.[especially the gparted resize operation can be time consuming]

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Good luck,and hope to see you again as a Ubuntu user.

---

