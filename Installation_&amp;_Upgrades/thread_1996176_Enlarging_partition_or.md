---
title: "Enlarging partition or?"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by speedy1wrc on 2012-06-03
I have a 160GB HD. I started with WinVista and repartitioned it to be able to install Ubuntu along  with Win. I thought I gave myself enough room, but at 11.10 I have run out of disk space. I can't install 12.04.

I got rid of a lot of stuff off my Win partition which is where I store all my data for Win and Ubuntu and resized my Win partition leaving me with 18g free in my extended partition where Ubuntu resides. 

I tried using Gparted to enlarge my current Ubuntu partions but I can't. The way the partitions are sandwiched together I can't resize any except the swap partition which is currently next to the unallocated space i just created. The ones I need to resize can't be because they are  tight together. 

I need to either be able to resize the needed partitions or clean out the current ones to give me enough room.

Which is the better option, and then the bigger question...how? I was primarily a Win user and and am much more familiar with it. I am slowly learning Linux, but am pretty much a novice still.

Thanks,
Mark

---

### Post by oldfred on 2012-06-04
Post screen shot from gparted. Attach with paperclip icon in edit panel above message. Then we can make specific suggestions.

Also mount all your partitions and post this from terminal to see amount used:
```

sudo df -h
```

I prefer to use smaller system partitions and separate data partitions. For years with XP I had a shared NTFS partition with Firefox & Thunderbird profiles & all photos. Then I used Firefox, Thunderbird & Picasa in both XP & Ubuntu using the same data. I still have that data in the shared NTFS even though now I boot XP rarely. Most new data goes into a ext4 data partition.

---

### Post by speedy1wrc on 2012-06-04
I'll do my best.

I have been running Gparted from CD,  so I'm not sure how to do a screenshot from that environment. 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             6.3G  5.5G  418M  94% /
udev                  1.2G  8.0K  1.2G   1% /dev
tmpfs                 492M  800K  491M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.2G  128K  1.2G   1% /run/shm
/dev/sda6             7.4G  6.0G  1.1G  86% /media/3d43e3d7-4242-4fb2-820b-3c39fc556c35
/dev/sda7             4.8G  705M  3.8G  16% /media/82fee960-6a3d-4ee6-b3e0-da90d3956e9d
/dev/sda2             8.5G  6.7G  1.8G  79% /media/HP_RECOVERY

I'm almost starting to think that uninstalling Ubuntu or reformatting the extended partition might be where I am headed. All my data is on the Win partition so other than a few settings it wouldn't be too bad. I did have trouble setting up the partitions to begin with, but if I get help ahead of time maybe it won't be too bad,

---

### Post by oldfred on 2012-06-04
Yes your root partition is small and starting to get full.

I like 10 to 25GB / (root) partitions with data either in a separate /home and/or other data partitions. Use NTFS if sharing with Windows for a data partition and set the Windows c: drive as read only to avoid Windows system issues or use ext4 for data if no Windows.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:

Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical
Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you have any data you want to save, back that up and erase all your Linux partitions. Just be careful not to erase the Windows partition. Use Windows to shrink the Windows partiton, but not create new partitons. The use gparted to create whatever partitions you prefer for Ubuntu.

The following article by the How-To Geek contains useful information regarding resizing your Vista partition, and getting it to boot again.
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by btwThieves on 2012-06-04
As much as it pains me to recommend a closed-source utility, EaseUS partition manager - from within windows - can probably fix you right up. It's been extraordinarily reliable and versatile, in my experience, and it's also a free utility.

---

### Post by speedy1wrc on 2012-06-05
Ok, I figured out how to install Gparted and use it from within Ubuntu.

I also went through the Gparted tutorial, and all is good.

The issue I think is that / is between 2 other partitions. The space I freed up is prior to /swap which isn't terribly useful. Trying to resize /dev/sda8 in a straightforward way seems unlikely.


[IMG]http://wnyllama.org/images/gparted.png[/IMG]

---

### Post by speedy1wrc on 2012-06-05
Doing a little more research it seems that /dev/ sda7 has a filesystem on it. It's mounted and appears as 5.1GB filesystem. There are 2 directories which are lost & found and mark. Mark has a full directory structure however it isn't being used. I created several files in documents and pictures and they aren't linked to my normal directories.

When installing 11.04 I believe it was, I manually created the partitions and following whatever directions I had it seems that I have an extra partition.

I am wondering if I delete that partition (/dev/sda7) and then it would allow me to resize my /mounted on /dev/sda8 partition, using that space. An extra 5GB would solve the current problem I have.

---

### Post by oldfred on 2012-06-05
That will work as long as you are sure you have no data to save. But it will not be a resize but a partition move. You do have to use the liveCD, so no partitions in the extended are mounted (little key shows mounted). You may have to swap-off to unmount swap as liveCDs like to use swap.

Moves take longer, and any power failure or other interruption will cause corruption or make for a total reinstall, so have good backups of whatever you want to save from sda8. If it is just an install then there is not much to backup as a reinstall will fix it.

I always do one task at a time in gparted, just to make sure it completes that one before the next. I have not had any issues with moves but do very few moves of partitions.

---

### Post by speedy1wrc on 2012-06-05
Ok, so I did a move and resize. that seemed to work just fine. However I ran into a boot issue since I deleted a partition and the remaining partition numbers were decremented by 1. 

I was left with grub rescue since grub also couldn't find the proper partition. Once I got that squared away I was able to configure grub to run and then get linux to boot. I installed boot-repair and all seems to be working fine now. 

It seems to be running much faster now and the next step is to upgrade to 12.04. 

If I find any other issues I'll post them up.

Thanks for all your help!

---

### Post by speedy1wrc on 2012-06-05
So here's where I am.

I just completed the 12.04 update and life is good.

It needs some tweaking, but that's to be expected.

Ready to rock and roll

---

### Post by speedy1wrc on 2012-06-05
Ehhh, it's sort of working.

I've had a problem with any modes other than Gnome with no effects and it's even worse now. 

I can't even boot to anything but Gnome no effects now. Grrr

---

### Post by wilee-nilee on 2012-06-05
> **speedy1wrc said:**
> Ehhh, it's sort of working.

I've had a problem with any modes other than Gnome with no effects and it's even worse now. 

I can't even boot to anything but Gnome no effects now. Grrr

Have you run in ubuntu, as far as picking up other installs? 
```
sudo update-grub
```
If you changed partition numbers you may not be getting the swap mounted have you checked that it is?

---

