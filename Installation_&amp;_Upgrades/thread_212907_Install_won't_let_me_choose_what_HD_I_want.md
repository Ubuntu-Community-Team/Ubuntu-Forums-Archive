---
title: "Install won't let me choose what HD I want"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by mod187 on 2006-07-10
I am installing 6.06 on an AMD 64 with 1G of RAM. This computer contains 3 hard drives and 1 DVD drive: 
IDE 1 Master is 120 GB
IDE 1 Slave is DVD
IDE 2 Master is 250 GB
IDE 2 Slave is 250 GB

I want to install 6.06 on IDE 1. There is an install of XP on one partition. I used gparted, and resized my XP partition to 40GB. I created a 3GB swap and the remaining space as 'ext3'. When I boot to the Live CD (either 386 or 64), it starts fine. XP still starts without problems. Only when I try to install, I get problems.

When I get to the partition screen, I choose manual mode. The only other option is to let ubuntu erase the entire disk, and I don't want to do that.

Under 'Prepare partitions', it shows me the drive hda1, with all of the partitions listed correctly. When I click 'next' to get to the 'Prepare Partitions' screen, it only lets me choose hdb or hdc as an install target. HDA is not listed at all (I think I should be looking for /hda2).

I tried disconnecting the second IDE channel so it would only find hda, and it worked. It took me through the install till 21% remaining, and then froze. I restarted, and the install was not there.

I would rather not install without the other drives being connected, but cannot figure out how to set it to let me use hda2.

I have also tried booting to gparted and removing the 'Boot' flag on the XP partition, placing the 'boot' flag in the ubuntu partition, and using not boot flag at all. All had the same results.

Any help would be great.

Thanks,

Matt

---

### Post by Athropos on 2006-07-10
Are you using the Desktop CD? If so, you should try the Alternate Install CD (equivalent to the previous 'normal' Install CD) which provides more control over partitions.

---

### Post by mod187 on 2006-07-10
Thank you for the QUICK reply...

I am using the desktop CD.

---

### Post by foots2015 on 2006-07-10
Try Using the Alternat install. It looks like you have better control over the partitions.

---

### Post by mod187 on 2006-07-10
I have already downloaded it. When I get off work, I'll try it, and report back with the results. Thanks for your help.

.\\OD

---

### Post by mod187 on 2006-07-11
OK. I ran the installation with the alternate CD. I selected OEM install.

The install ran smooth. I had to delete the ext3 and swap partitions I made with gparted, and let the install create them for me. Once installed, I removed the CD and restarted.

The first thing I noticed is that XP was not listed in grub, but no big deal. I can fix that later.

Once I got to the ubuntu splash screen, the problem started. As it started, it listed:
Loading Essential Drivers     OK
Mounting Root File System
Waiting for Root File System

It froze here for about 5 minutes (it felt like). Then it took me to the text screen. Here, it told me:
Alert! /dev/hda2 does not exist. Dropping to shell
Decompressing Linux
(I installed this on hda2. It named swap as hda5 for some reason)

The next line read:
/bin/sh: can't access tty; job control turned off

Where I stand now? I deleted the partitions, and repaired my MBR. I am ready to start over- I hope someone can steer me in the right direction.

Matt

---

### Post by mod187 on 2006-07-20
I have also tried to install with the x86 CD. No luck. Same partition problems.

If I install kubuntu, and apt-get install ubuntu-desktop, will it allow me to choose from kubuntu, ubuntu, and XP when booting, or will it overwrite kubuntu with ubuntu?

Does anybody else have any ideas?

.\\

---

### Post by orb9220 on 2006-07-20
During the partioning menu did You go up and use the drop down menu to select
the hd you are partitioning. Since I had two hardrives I can go to the top right of gpart and select which drive I want to part.

It is a drop down menu in top right corner.

Just a thought.

---

### Post by mod187 on 2006-07-20
When all 3 hard drives are connected, it shows all 3 from the drop down list. I will select hda (I want to use) and set the size, but once I go to the next page, the only drives listed are hdb and hdc.

When I disconnect hdb and hdc, it only listed hda (the first time I tried to install without the other drives connected). I tried to install this way, and it crashed (see first post). 

I have since tried to install again with the other drives disconnected. I will select hda under the prepare partitions page, and when I click next, it lists no drives. The box to set mount points is there, and the box to select drive is there, but they are empty.

.\\

---

### Post by mod187 on 2006-07-21
I tried it again last night. I have got to get this running.

First, I tried to install with the alternate 64 install disc in text mode. I got the same problems. OS will not load.

         On a side note, the install does not find any other operating systems during install, and will not setup Grub to include them. 5.10 did, as well as the kubuntu install I did on my P4.

I then tried to install kubuntu. Install went better than ubuntu, but grub did not find XP, and the OS still hung at 'Waiting for Root File System' (read 6th post in thread).

At that point, I decided that 6.06 is not ready for my machine, so I installed 5.10, only to find the same problem.

5.10 found my xp install, and setup grub for it. But when I try to boot to ubuntu, it hangs at the 'Waiting for Root File System', but only for a split second, the drops me to a prompt.

> Alert! /dev/hda2 does not exist. Dropping to shell
Decompressing Linux

/bin/sh: can't access tty; job control turned off

Could this be something with my hard drive, or is my motherboard just not linux friendly? I have this sweet AMD 64, but will move my p4 back over to my desk if I need to.

---

### Post by mod187 on 2006-07-26
I became convinced that the problem was with the way XP formatted my hard drive originally. So this is what I did next:

I removed IDE 2 master and slave drives, so I only had 1- 120G hard drive and 1 CD drive on IDE 1.

I then added an old 60G drive to IDE 2 master. Using gparted live CD, I copied my XP partition to the 60G drive. (I then removed all drives, and restarted XP on the 60G to make sure the copy worked, and it did. (for those who need to know) I did have to boot to the XP CD and repair the master boot record) Gparted is the shiznet...

OK, once I knew the copy worked, I replaced my 120G HD with the original XP install, and using gparted I deleted all partitions. I then copied my XP partition back from the 60G to the 120G (to a 60G partition), and booted/repaired mbr to make sure it worked. It did.

Then the breakthrough-

I booted to the Live CD (64) and it loaded fine. When I went to run install- IT WORKED! It let me choose what partition/drive I wanted (in this case, it was the 60G left over on the 120G drive after the XP Partition, with a 2G swap). The install completed, and after restarting…

I was left with the same error as before:

> Alert! /dev/hda2 does not exist. Dropping to shell
Decompressing Linux

/bin/sh: can't access tty; job control turned off

I don't know anything about Busybox.

I read a couple of post that say the install renames all drive, and suggested to change the command in GRUB from hda2 to hd*2 (I tried e, b, c, f- I have 3 hard drives with a total of 5 partitions and 1 CD drive)

Despite  my better efforts, I still get the same error.

I tried kubuntu, with the same results.

After reading
[http://www.ubuntuforums.org/showthread.php?p=1284341#post1284341](http://www.ubuntuforums.org/showthread.php?p=1284341#post1284341)
I tried to install 5.10 and upgrade, but got the same error. It installed fine, set up GRUB great, but still drops to BusyBox.

Any new ideas?

I think I may try to install 6.06 on my 60G drive, to see if it is the 120G drive itself. I don't know how to install XP after Linux- every time I tried in the past, XP takes over, but I'm sure there is a way.

Any help/thoughts would be great

.\\

---

### Post by mod187 on 2006-07-26
Dear Diary,

Today I tried a new hard drive. I disconnected my 120G, and connected only a 60G hard drive to IDE 1 master and CD to IDE 1 slave. I left IDE 2 as it was. I installed with the ubuntu alternate CD, and when restarting, it failed to mount file system: hda1 does not exist.

I booted to the live CD, and checked to see what it listed the drives as. The drive in question was listed as hda1, so I restarted and checked it again. I then told GRUB to boot from 'hda, hda1, hda2, hdb, hdb1, hdc, hdc1, ... hde2, with no luck.

Is there a way for BusyBox to tell me what drive is mounted as what? I feel like if I boot the live CD, it will label the drives how the live CD wants them, not as how the install and/or GRUB has labeled them...

---

### Post by mod187 on 2006-07-29
I woke up this morning and, for some reason, unplugged ALL IDE devices from my computer, and plugged in ONLY the 60G HD I played around with earlier. Remember?

> 
*Today I tried a new hard drive. I disconnected my 120G, and connected only a 60G hard drive to IDE 1 master and CD to IDE 1 slave. I left IDE 2 as it was. I installed with the ubuntu alternate CD, and when restarting, it failed to mount file system: hda1 does not exist.*

With the CD drive removed, and no devices on the second IDE channel, ubuntu loaded. Perfect.

So, now I have these items to think about:
These hardware items are not the issue:
Motherboard (LAN, sound, video)
60G HD

These hardware items are questionable:
120G HD (tomorrow I will test to see if it will install and run on the drive without XP, only ubuntu)
DVD Burner (I don't want to give up my Lite-On... It's the only thing that can burn movies the way I want them)
Two 250G HD's (I have a buttload of stuff on one, and the other is a backup of the first)


I have never installed XP AFTER Linux, but this may be the way to do it. I will find out tomorrow...

(By now, I wish this thread had a new title)

---

### Post by mod187 on 2006-07-31
First, let me mention the USB theory. I have not mentioned if I removed all USB devices during install or not, but I did in fact remove all USB devices, and this did not solve my problem.

I did, however, get it to work.

It was my hard drive.

My last post, I narrowed it down to my HD, CD, and spare HD's. I completely wiped out my 120G drive (removed XP partition) and installed Live CD and Alternate CD. Both failed. I then replaced the 120G HD with the 60G, installed the Alternate CD, and it worked.

The drive is a Maxtor DiamondMax Plus 9 120G ATA/133
m/n:6Y120P0131211

Final configuration was:
IDE 0 Master- CD (pins set to master)
IDE 0 Slave- HD (60G: 20G XP, 30G ubuntu, 3G Swap) (pins set to slave)
IDE 1 Master- HD (250G Docs and stuff) (pins set to master)
IDE 1 Slave- HD (250G backup of IDE 1 M) (pins set to slave)

I don't know if 'Cable Select' setting makes a difference or not, but I know it works this way.

Later, I'll post my mother board info, so if someone else has this problem, they can compare.

Thanks to those who looked- props to those who replied.

---

