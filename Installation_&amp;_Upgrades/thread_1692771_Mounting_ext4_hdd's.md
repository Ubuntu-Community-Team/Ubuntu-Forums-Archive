---
title: "Mounting ext4 hdd's"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by -RYknow on 2011-02-21
Hey guys. I'm having a little bit of a problem. I'm in the process of switching all my hdd's over to ext4. I have 3x1TB, and 2x2Tb drives, as well as a Raptor X for the OS. Two of the drives have already been formatted to ext4, and the rest are NTFS. 

I'm to the point of trying to get the drives mounted. I followed through [this]("http://www.psychocats.net/ubuntu/mountlinux") guide. It didn't turn out quite as I had hoped. The drive is working, and I can copy files to it. But in order to get to the drive I have to go to my computer, click filesystem, and then scroll down till I find the drive. Basically I want to find out if this is normal? And if it is, what do I need to do to have the drive mount to the desktop on startup?

Any help would be great! 
Thank you, 
-RYknow

---

### Post by mikewhatever on 2011-02-21
Everything mounted under /media/ will show on the desktop, and everything else will not. The guide you followed shows the mount point as /storage, change it to /media/disk1, /media/disk2, etc.

---

### Post by -RYknow on 2011-02-22
How would I go about changing it's mount point (can you give me an example of the command?)? Sorry for the lame question...still learning linux. This is my first experience running drives with ext file-systems instead of ntfs.

Thanks, 
-RYknow

---

### Post by mikewhatever on 2011-02-22
Look at the guide you linked to again. Everywhere it says '/storage', replace it with your own mount point, for example, /media/disk1, /media/disk2, etc, the point of it being that the mount points (disk1 and disk2) are in the /media directory.

---

### Post by -RYknow on 2011-02-22
Ok great! I see how this works now. I have a few drives already setup! In the process of moving data around so I can finish switching all the drives over to ext4. 

I do have two more questions. First off, how can I get rid of the drive showing up when I first click on filesystem? It's showing up in /media/xxx as it should, but I'd like to remove it from the original location I put it. The command I used to get it there was *mkdir /TV3*. 

My other questionwas about the guide I used. The person who wrote the guide talks about using the uuid when mounting the drive. I just used it's assigned location (/dev/sde1). Is this an issue, or should this work just fine?

Thanks again! You've been a big help!
-RYknow

---

### Post by mikewhatever on 2011-02-22
> **-RYknow said:**
> ...

I do have two more questions. First off, how can I get rid of the drive showing up when I first click on filesystem? It's showing up in /media/xxx as it should, but I'd like to remove it from the original location I put it. The command I used to get it there was *mkdir /TV3*. 

As said above, you remove it from the mount point /TV3 by changing the mount point to, say, /media/TV3. Same goes for all the lines you've created in fstab. If you want help with that, post the output of:
```
cat /etc/fstab
```

> 
My other questionwas about the guide I used. The person who wrote the guide talks about using the uuid when mounting the drive. I just used it's assigned location (/dev/sde1). Is this an issue, or should this work just fine?


Theoretically, it should work, at least as long as you don't add partitions or rearrange the hdds. /dev/sde1 designation is assigned according to the order the bios sees the hdds, but rearrange them, and a different partition might get /dev/sde1. With UUIDs, each partition has its own unique id number and therefore will always be mounted to the same mount point.

---

### Post by -RYknow on 2011-02-23
Thank you for all your help! Everything is up and running as it should be! I appreciate your patience and all your help! :mrgreen:

Thanks again!
-RYknow

---

