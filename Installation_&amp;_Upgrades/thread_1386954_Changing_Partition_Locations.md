---
title: "Changing Partition Locations"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by gcvisel on 2010-01-21
I have been using Ubuntu since the Dapper Drake, and at one point had a non-recoverable crash that caused me to reinstall it in a second partition and copy data over.
 
I have since blown away the original partition and have a sizeable unused space on the HD "down at the left end" as viewed with Gparted. 
 
How do I now reclaim that unused space?  Using Gparted while logged in of course locks the active partitions.  I would rather not screw up this partition...  ;-)
 
Thanks,
Spook

---

### Post by ks07 on 2010-01-21
Your best bet is to (after backing up anything important just in case, ofc) boot from a Live CD and use GParted from there. If it automatically mounts any partitions (such as swap), you can unmount them from GParted without a problem.

---

### Post by darkod on 2010-01-21
Yes, using Gparted from live desktop will do the trick, but only halfway. I helped someone with this issue few months ago, but can't remember the command now.
Gparted will only expand the partition but not the actual extN filesystem. There is separate command that you use to expand the filesystem after that, or your root partition will remain at the current XX GB.
Try googling about expanding/resizing ext2/3/4, I can't remember the command. :)

---

### Post by oldfred on 2010-01-21
I have become a fan of having data partitions. You may want to just create a new partition for all the space and make it a data partition. You then can mount and use the data partition just as additional storage as if it is folders in /home.

---

### Post by gcvisel on 2010-01-21
> **oldfred said:**
> I have become a fan of having data partitions. You may want to just create a new partition for all the space and make it a data partition. You then can mount and use the data partition just as additional storage as if it is folders in /home.
    Why would you do that, Old Fred?  What problems do mixing data with the OS cause?
 
Spook

---

### Post by blackened on 2010-01-21
> **darkod said:**
> Yes, using Gparted from live desktop will do the trick, but only halfway. I helped someone with this issue few months ago, but can't remember the command now.
Gparted will only expand the partition but not the actual extN filesystem. There is separate command that you use to expand the filesystem after that, or your root partition will remain at the current XX GB.
Try googling about expanding/resizing ext2/3/4, I can't remember the command. :)

Change the italicized text to match your partition designation.
```
resize2fs -p /dev/*sdxx*
```

---

### Post by blackened on 2010-01-21
> **gcvisel said:**
> Why would you do that, Old Fred?  What problems do mixing data with the OS cause?
 
Spook

It gives you the ability to reinstall the OS from scratch without having to format the data partitions or drives. I usually specify a root, home, and data partition during installation for this very reason.

**Edit:** sorry about the double post, I should pay more attention.

---

### Post by gcvisel on 2010-01-21
Originally Posted by **darkod** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8701079#post8701079") 
[I]Yes, using Gparted from live desktop will do the trick, but only halfway. I helped someone with this issue few months ago, but can't remember the command now.
Gparted will only expand the partition but not the actual extN filesystem. There is separate command that you use to expand the filesystem after that, or your root partition will remain at the current XX GB.
Try googling about expanding/resizing ext2/3/4, I can't remember the command. :smile:[/I]

> **blackened said:**
> Change the italicized text to match your partition designation.
```
resize2fs -p /dev/*sdxx*
```
 Will it matter that the empty space is at the beginning of the HD, (where I deleted the old copy of Ubuntu from?)  Does Resizing like that also move the data, or does this matter?

---

### Post by oldfred on 2010-01-21
I had a standard root and swap only install (with some data in an NTFS partition for windows sharing) and upgraded for three years. Every update required effort to get it working right. This time I followed the idea of separate /home and another for data. I moved home and kept my old install (as backup of configs) and did a clean new install. I now am not sure I even need a separate /home as it is only 1GB and still has some of the 3 years of cruft in it. All my data is in data partitions and I link into home. With the separate data partitions the install was very easy.  And now my OS partition(s) are small enought I will alternate every new install in case there are some old settings I want.

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by blackened on 2010-01-22
> **gcvisel said:**
> Will it matter that the empty space is at the beginning of the HD, (where I deleted the old copy of Ubuntu from?)  Does Resizing like that also move the data, or does this matter?

No, it doesn't matter if the space is before or after the original partition. Use gparted to grow the partition into the unallocated space, then use the resize2fs command to grow the filesystem to fit the partition. 

Gparted may run resize2fs on its own, in which case you won't need to run it again. Just keep an eye on the progress details as it works.

---

### Post by gcvisel on 2010-01-25
> **ks07 said:**
> Your best bet is to (after backing up anything important just in case, ofc) boot from a Live CD and use GParted from there. If it automatically mounts any partitions (such as swap), you can unmount them from GParted without a problem.
 
I tried this last night. It was going swimmingly, booting to the CD, starting Gparted, unmounting the main drive, resizing and moving the main partition, until...
 
In the middle of the final 1.5 hour bit-by-bit copy of the data down to the new location, the laptop rebooted! It came back to a login screen which did not recognize my ID and password. 
 
I rebooted again to the CD, and now see what looks like a kinda clean install of Ubuntu with, (you ready for this?) two recent backup folders! At that point, it was past midnight and I was tired, and I let it rest. :-(
 
I do not believe I can boot to the hard drive, and I'm not at all sure I want to create a small boot partition that I could download the backup program to. 
 
Anybody got suggestions for how to recover from this fiasco? I do have a desktop that I can network with, (if I can get access to my network with this machine.)  The desktop is older and has a smaller HD, (80 gig?) so I had not backed up to that machine.  Probably should have.  (Gotta get an external drive for this!)
 
I'm definitely in the Go Slow mode, not wanting to screw it up further!
 
Thanks,
Spook

---

