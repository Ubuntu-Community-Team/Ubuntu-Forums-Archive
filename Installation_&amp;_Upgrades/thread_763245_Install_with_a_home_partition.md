---
title: "Install with a home partition"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by dover19 on 2008-04-22
I've read that you can have a home partition for Ubuntu so that whenever a new version comes out you can do a clean install instead of just upgrade and you will keep your setting after doing the clean install rather than losing everything.

I've looked around but couldn't find a simple HOW TO that a linux noob could understand. I actually have Ubuntu  installed right now as well as XP and I would like to re-install Gutsy cause I've screwed something up after playing around with it for the first time and I'm not even sure how I could do THAT.

Thanks

---

### Post by Pumalite on 2008-04-22
I assume you are using Grub to dual boot. Post:
sudo fdisk -l

---

### Post by dover19 on 2008-04-22
Yep, I'm using Grub to dual boot.

Here's my fdisk -l:

> Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d340d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12988   104326078+   7  HPFS/NTFS
/dev/sda2           12989       24415    91787377+  83  Linux
/dev/sda3           24416       24792     3028252+   5  Extended
/dev/sda5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67bd6faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3d24c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by Pumalite on 2008-04-22
Use Gparted Live CD. Burn to disk and boot from it. Delete Ubuntu (sda2, sda3 and sda5). Make it 'free space'. There, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (in laptops, /swap=RAM)
The rest for /home.
Install Ubuntu, go Manual and use already prepared partitions.

---

### Post by dover19 on 2008-04-22
Ok, sounds straightforward enough...sort of, lol.

I'm just wondering do I name these partitions in Gparted ("/","/swap" and "/home") and when I go to install manually Ubuntu will detect what the home partition because I've named it "/home"?

Where am I installing Linux, on "/"? I guess this is what I'll be formatting the next time I want to re-install Ubuntu right? All my settings and Beryl and all will be on the "/home" partition.

Just trying to grasp exactly how this works, I've only been playing around with Ubuntu for less than a week.

Thanks

---

### Post by Pumalite on 2008-04-22
Once you go Manual and make the partitions with their mount points, you press 'Forward' and the installer will take care of everything for you.

---

### Post by ace007 on 2008-04-22
There is a perfect guide for what you are asking in the link in my signature.


[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dover19 on 2008-04-23
That's the site I was looking at and I can't understand what to do. I'm mostly not sure which is my situation. Because I have Ubuntu already installed, but I want to format it to have a clean install because I've screwed some things up.

So if I use the "Ubuntu is already installed" method and create a home partition and then re-install Ubuntu after, won't my home partition keep all the "screwed up settings" and make it pointless for me to re-install?

And if I use the "Ubuntu is not yet installed" option it takes me t page that explains how to do a dual boot installation. But that's not right either, because I already have a dual boot installation, I don't want to make another one.

I was just completely confused trying to use the guide from psychocats.

---

### Post by halw on 2008-04-23
> **Pumalite said:**
> Use Gparted Live CD. Burn to disk and boot from it. Delete Ubuntu (sda2, sda3 and sda5). Make it 'free space'. There, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (in laptops, /swap=RAM)
The rest for /home.
Install Ubuntu, go Manual and use already prepared partitions.

Since you will be reinstalling, follow these instructions from Pumalite. You don't necessarily need to use Gparted Live cd. Any live cd will work if it has gparted on it.

---

### Post by ace007 on 2008-04-23
well it depends on what is screwed up.  The home partition is like a windows documents and settings folder.  It contains My documents and a few application settings.

---

### Post by ace007 on 2008-04-23
> **Pumalite said:**
> Use Gparted Live CD. Burn to disk and boot from it. Delete Ubuntu (sda2, sda3 and sda5). Make it 'free space'. There, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (in laptops, /swap=RAM)
The rest for /home.
Install Ubuntu, go Manual and use already prepared partitions.

These are the steps you need to follow.  If you are having difficulty with these instructions, then maybe you should just do a regular install of Ubuntu without placing the home partition in a different place.  The task might be a little to advanced for you.  After a while, when you are more advanced you can move the /home to a new partition at a later time.

You can use this tutorial after you have installed Ubuntu to move the partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by zero244 on 2008-04-23
Setting up a Home partition is a good idea. It wont make a upgrade completely painless but it will save you some time tweaking things and it will save files youve collected like music or whatever without formating everything if you dont have a separate /home partition.
I havent even looked at a beta version of Hardy yet. I am still using Edgy and Feisty at the moment.
They are both working very well not sure if I want to mess with a perfectly working version of Ubuntu just to have the latest version.

---

### Post by addisor on 2008-04-24
I'm about to embark on a clean install of Hardy, and am interested in tidying up my two HDD's. At the mo I have 6.10 (now unused) on HDA and 7.10 on SDA. Is it conceivable that I have ended up with two Home partitions? How can I ckeck, here is my fdisk, Bit of a mess I feel? I'd like to install hardy over 7.10 and make HDA the home partition.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe366e366

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+  83  Linux
/dev/sda2            2933        5864    23551290   83  Linux
/dev/sda3            5865        8796    23551290   83  Linux
/dev/sda4            8797        9433     5116702+   5  Extended
/dev/sda5            8797        9433     5116671   82  Linux swap / Solaris

---

### Post by Bartender on 2008-04-24
For those of you asking about partitions and unsure what you have and how it's set up (swap, /, /home) I think the simplest way to get help is to toss in a LiveCD, go to the partitioner, and take a screenshot of your partition map.  It's easy to take a screenshot - before going into the partitioner, plug in a thumb drive and wait for it to be recognized on the desktop.  Make a note of its description.  Go into partitioner, wait for the map to come up, go to Accessories > Take Screenshot, save the entire desktop or the window, and save it to the thumb drive.  Get out of the Live CD, come on back here and attach the screenshot.  We can then tell you in about one second whether you already have a /home partition, etc.
I still prefer the stand-alone GParted LiveCD for doing the actual partitioning work.  You can take screenshots from the stand-alone CD but it's so much easier from an install LiveCD.  So, use the installer CD to take a couple of screenshots, but use the stand-alone GParted LiveCD for actual partitioning.

If you do as suggested in this thread and set up the three partitions first with the stand-alone CD, here's what I do - make one extended partition.  That way you don't box yourself in by making too many primary partitions.  Remember, four is the limit and GParted will likely get uncooperative if you try to make that fourth primary.  Once you've created the extended partition, create a partition inside for /, formatted as ext3.  Create another one for swap, formatted as linuxswap.  Create a third partition for /home, formatted ext3.  This takes some scratching around in the GParted menus but it's not technically hard, just a matter of familiarization.  The sizes are up to you.  If you have lots of room don't sweat it.  10 to 30 GB for /, a gig or two for swap (the more RAM you have the less likely your PC will use swap at all), the rest for /home.  If you don't have a lot of room then you need to be more careful about how much to allocate for / and I don't have a bomb-proof recommendation.  Write down the labels for each partition.  Let's say for the sake of this discussion that sda6 is /, sda7 is swap, sda8 is /home.  Write it down.  You do not want to be guessing during install!
Then, when you're ready to install, go into manual partitioning.  sda6 is the / partition that you already set up.  Click on it and the installer will say something about "inspecting" or "preparing", I don't remember exactly.  You want to click the format checkbox on so that it will format the partition, and you want to go into the "mount point" dropbox and check "/".  
It's important to realize that you can change or wipe out the settings you made during the previous steps where you prepared the HDD for installation with the stand-alone partitioner or the LiveCD partitioner.  When you made the partitions and set their mount points, that was like setting the table for the installer.  It's up to you whether the installer sets down to the table and acts politely or whether it smashes the china and tosses the silverware against the wall.
OK, so back to the story - you're in the manual installer now, you've told it to format sda6 and told it to mount sda6 as /.  Once you're done it should go back to the main partitioner menu, where you can point the partitioner at sda7, tell it to format (it'll format the swap whether you tell it to or not), then mount that partition as swap.  Same thing with sda8.  Tell it to format, mount it as /home, then you should be ready to leave the partitioner and continue with install.

If you've already built a /home partition and it has personal data on it, there is one crucial change to the above - when in the install process, make sure to mount that existing partition as /home, and make *absolutely sure* that the format checkbox is unchecked, not checked.  You do not want the installer to wipe the /home partition!

---

### Post by addisor on 2008-04-24
screenshot as attached

---

### Post by Pumalite on 2008-04-24
Mix of SATA and IDE. Bad news:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by addisor on 2008-04-25
Thanks, but can I put hardy on sda1 and make hda /home and delete the boot flag.

---

### Post by Pumalite on 2008-04-25
You should then make sda first boot in BIOS after CD-ROM

---

### Post by addisor on 2008-04-30
just thought i'd report back on sucess, hda1 (now sda1)is now a single ext3 partition, sda1 is now sdb1 as / sdb2 is /home and 2gb swap, hardy heron installed a treat.

---

### Post by Pumalite on 2008-04-30
Success is hard to beat.

---

### Post by Fury161 on 2008-04-30
So... What are the benefits of installing /home separately?

---

### Post by Pumalite on 2008-04-30
You get vto keeps all your settings and stuff in case you need to reinstall.

---

