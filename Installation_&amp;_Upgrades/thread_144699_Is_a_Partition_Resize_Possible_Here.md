---
title: "Is a Partition Resize Possible Here?"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by bluevoodoo1 on 2006-03-14
I'd like to reduce my swap partition to 1 gig, take off 2 gigs of my /home and add the 3 gigs to /. I've booted up a Live CD's gparted and it seems that I can only reduce the sizes of each of partitions in question, but not add anything back to any of them.

From what I've read, you can take space from the end of each, but not the beginning right? Here's my /etc/fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       /home           ext3    defaults        0       2
/dev/hdc6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Is having my / partition as hdc1 not letting me do this and is it possible to change things without doing anything too risky? (copying/deleting partitions)

---

### Post by az on 2006-03-14
You may only resize partitions from the beginning.  You would have to delete the swap, shrink your home and  move it higher up (if you can) and then extend your "/", move your home back to where the new end of your / is and then recreate your swap.

I'm an all-on-one-partition kind of guy.....

What are the sizes of the current partitions?

---

### Post by bluevoodoo1 on 2006-03-14
```

/dev/hdc1             4.6G  2.6G  1.8G  59% /
tmpfs                 474M     0  474M   0% /dev/shm
tmpfs                 474M   13M  462M   3% /lib/modules/2.6.12-10-686/volatile
/dev/hdc5              67G   53G   11G  84% /home

```

Swap is 2 GB. I have 1 GB of ram, and I've never used more than 12 mb of swap (so conky tells me). 

> I'm an all-on-one-partition kind of guy..... 
Yeah, my older computer with Breezy is just one partition, definitely wouldn't be having this problem, but a fresh install would wipe it clean. 
Right now, I just want to make sure I have room for Dapper and any other future upgrades/apps. So it's just preparation for that. If my DVD burner worked, I'd just back everything up and do a clean install when Dapper came out. That's why I'm not certain if I want to mess with anything here, since the potential for data loss seems inevitable. 
I've been trying to clean up "/" by getting rid of some kernel sources the never worked out and the like. But since the burner isn't working yet, I'm hesitant to do anything, but still anxious to install Dapper. Normally I don't like gushy sort of "eyecandy" but after playing with the Kororaa Xgl LiveCD I'd really like to install Dapper and "mess around." But even if I don't install it now, after its official release, it will be a must.

---

### Post by red_shrike on 2006-03-15
Damn, I am having the same problem. I was thinking of running Knoppix and qparted, or doing it from Win... Will it be a problem if partitions are formated in different file systems? My / is jfs and /home is ext3

---

### Post by bluevoodoo1 on 2006-03-31
[QUOTE=azz]shrink your home and  move it higher up (if you can) ?[/QUOTE]

Well, I've tried moving up /home but it seems like I can't. I don't think there are any acrobatic moves I can do here... in the end I should have put / right next to /home.
Here's a screenshot from gparted if anyone has any ideas...

---

### Post by Herman on 2006-04-01
I agree with azz, but will be a little more verbose to make it clearer.
You will have to remove around 20 or 30 GB of data from hdc5 before you can start. (Now that we see your GParted thumbnail).
If you choose to delete the swap area temporarily, you will have a little more room to copy and paste your /home partition and might not have to remove quite as much data, so deleting the swap is a good idea.
Then resize hdc5 to less than half the size it is now, between half and one third of its present size would be best. 
Then you will have hda5 with a large area of free space behind it.
Copy hdc5 and paste it  to the end of the free space. It will have a new partition number, probably hdc6, the number your swap used to have, ignore that for now.
Delete the original hdc5 to give you room to  resize hda1  (/) larger. 

Then copy hdc6 back to the end of hda1, it will be given the number hdc5 once again, like it had before. 
You can delete hdc6 now, and make your new swap area, which will now be given the number hdc6 again, like your old swap area used to be called.
Finally, resize hdc5 to fill the free space and you are done.

The reason why all this copying and pasting is necessary is because you cannot simply 'move' Linux partitions. Linux partitions can only be moved by copying and pasting somewhere else, but then they will have a new partition number. 
By copying and pasting a second time so that it gets its old partition number back again, it saves having to re-install the GRUB boot loader and edit /etc/fstab
(It is not very difficult to re-install grub and edit /etc/fstab if you do decide to leave the partitions with different numbers than they had before).
I call this 'partition leapfrog'. It's not very complicated once you try it, but explaining it or reading it explained may seem complicated unitl you do it once, then it will all make sense.
I prefer single partition installs myself, they are a lot tidier and simpler to work with. 
It would be easiest and best to use GParted LiveCD if you are not already, see my second sig link for where to download the .iso for one. Regards, Herman :D

---

### Post by bluevoodoo1 on 2006-04-01
Thank you Herman for you reply. That is exactly what I needed! I will start backing up my data and attempt the resize. I have the GParted LiveCD all ready to go! I will write back with any news! Thank you again!!

---

### Post by chrismyers on 2006-04-18
I just stumbled across GPLed - Partition Magic clone.

I found it here:

[http://www.jankratochvil.net/project/surprise/](http://www.jankratochvil.net/project/surprise/)

Will this help?

---

