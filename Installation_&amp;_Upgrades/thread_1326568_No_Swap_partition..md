---
title: "No Swap partition."
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by blegs38552 on 2009-11-14
I installed Ubuntu 9.10 from the alternate installation CD on a dual boot HDD with Windows 7. For whatever reason, and I was going around in circles at the point of creating my linux partition, no swap partition was created. The Ubuntu partition is a Linux ext4 partition.

What is the best way to create the swap partition short of uninstalling and reinstalling the O/S? I am somewhat of a newbie, so I would appreciate specific direction as a mis-step could probably hose my Ubuntu installation (and maybe my Windows one too).

---

### Post by scragar on 2009-11-14
OK, this is a quick guide on creating a 512MB swap, just change the numbers if you need more:

First, create the swapfile:
```
sudo dd if=/dev/zero of=/mnt/my.swap bs=1M count=**512**
```
Then make it a swapfile:
```
sudo mkswap /mnt/my.swap
```
And then start using it:
```
sudo swapon /mnt/my.swap
```

To make it mount automaticly you need to edit the fstab.
```
echo "/mnt/my.swap  none  swap  sw  0 0" | sudo tee -a /etc/fstab
```

To make the file 1GB increase the size to 1024 instead of 512 in the first line.

---

### Post by dhavalbbhatt on 2009-11-14
> **blegs38552 said:**
> I installed Ubuntu 9.10 from the alternate installation CD on a dual boot HDD with Windows 7. For whatever reason, and I was going around in circles at the point of creating my linux partition, no swap partition was created. The Ubuntu partition is a Linux ext4 partition.

What is the best way to create the swap partition short of uninstalling and reinstalling the O/S? I am somewhat of a newbie, so I would appreciate specific direction as a mis-step could probably hose my Ubuntu installation (and maybe my Windows one too).

Use GParted on LiveCD to create a new partition. I would also suggest that you carve out some space from your Ubuntu partition as against your Windows partition (Windows has fragmentation issues, which you don't want to get into).

---

### Post by scragar on 2009-11-14
> **dhavalbbhatt said:**
> Use GParted on LiveCD to create a new partition. I would also suggest that you carve out some space from your Ubuntu partition as against your Windows partition (Windows has fragmentation issues, which you don't want to get into).

Resizing partitions causes problems with UUIDs, creating a swapfile as I recommended is the much cleaner path.

---

### Post by darkod on 2009-11-14
Even if you can create swap partition now I;m not sure you can point ubuntu to it because it's already installed.
Another option I've heard is to actually have a swap file similar like windows does. Don't know exact steps but wouldn't be difficult to find a tutorial in google. Creating the swap file sounds easiest at the moment.

---

### Post by darco on 2009-11-14
How much memory do you have installed? If you have at least 6-8gigs, you dont even need swap. I'm running KK w/o swap on 8gigs and I see no performance lost. If you have a laptop, you would need swap for hibernation...

darco

---

### Post by blegs38552 on 2009-11-14
OK to all - let's see if I can address all of the replies.

I followed scragar's steps, and did not get any error messages. However, I do not see any evidence that a swap partition was actually created. I rebooted just to make sure - is there anywhere in Ubuntu that I should see this? I also looked in Windows Computer/Disk Manager which shows the Linux partition but not a wap partition. I only have 2 gig RAM installed, which is the maximum that the computer will support (a 3 year old Gateway), so I am stuck with it. 

The Gparted LiveCD sounds like an interesting option, but I would like to have a confidence level regarding the UUID problem (on the other hand, this is a dual boot PC, and Windows 7 is my primary O/S, so as long as that does not get hosed, there should be no lasting problem).

---

### Post by scragar on 2009-11-14
```
free -m
```
Will show that swap is on.
For example, my output with 5GB of swap(So I can hibernate with 4GB of ram)```

             total       used       free     shared    buffers     cached
Mem:          3834       2755       1078          0        145       2031
-/+ buffers/cache:        578       3256
**Swap:         5004         11       4993**
```As long as the bottom line isn't all 0s then swap is on.

---

### Post by JohnnyVW on 2009-11-14
> **blegs38552 said:**
> OK to all - let's see if I can address all of the replies.

I followed scragar's steps, and did not get any error messages. However, I do not see any evidence that a swap partition was actually created. I rebooted just to make sure - is there anywhere in Ubuntu that I should see this? I also looked in Windows Computer/Disk Manager which shows the Linux partition but not a wap partition. I only have 2 gig RAM installed, which is the maximum that the computer will support (a 3 year old Gateway), so I am stuck with it. 

The Gparted LiveCD sounds like an interesting option, but I would like to have a confidence level regarding the UUID problem (on the other hand, this is a dual boot PC, and Windows 7 is my primary O/S, so as long as that does not get hosed, there should be no lasting problem).

Actually, scragar's method doesn't create a swap *partition*, it creates a swap *file* kind of like windows does it.  It should work the same.  Nice way of doing it without messing with partition resizing.

As far as seeing the swap, a very quick point-and-click way would be to look at the System Monitor (System > Administration > System Monitor).

---

### Post by blegs38552 on 2009-11-14
total       used       free     shared    buffers     cached
Mem:          1948        304       1643          0         26        102
-/+ buffers/cache:        176       1772
Swap:         2047          0       2047

Looks like it's working.

System Monitor is show 0 of 2 GB for swap history.

I guess a swap file is as good as a swap partition - it's worked for Windows since time immemorial. 

Guess the best way to test is to try and hibernate.

Did not hibernate as Windows does- more like a sleep mode. Computer did not totally shut down, but screen blanked out. Pressing the power button prompted me for my password. The screen came black, albeit somewhat im. I had to use the laptop's screen brightness control to restore it to normal.

Thanks to all.

---

### Post by movieman on 2009-11-14
> **blegs38552 said:**
> I guess a swap file is as good as a swap partition - it's worked for Windows since time immemorial.

The primary benefit of a swap partition is performance: you cut out the filesystem layer and you know that it's always contiguous on the disk.

The downside is that you'll almost always have to seek from your data partition to the swap partition to access it, so in some cases a swap file may be faster (e.g. if you've just been reading a data file which is close to the location of the part of the swap file you need). Plus, of course, you can't easily increase the size of the swap partition, whereas you can trivially increase the size of a swap file.

---

