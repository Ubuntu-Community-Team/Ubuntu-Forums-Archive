---
title: "no root file system"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by mcraehutch on 2006-11-16
I'm attempting to install ubuntu and am running into a problem. I have a 10gig partition free and already have a swap partition. During install I assign the / partition and it already recognizes the swap. When I click next, it states I haven't designated the root file system (although I have).
Now, when I was at the graphical partition tool it showed my entire hard drive as unallocated, which is not the case. My hard drive is very fill except for the 10gigs allocated to this install. From there, when I'm at the point of assigning the mount points, it does see my partitions in the drop down box. This is where I assign root to sda7 in my case. This partition is a logical partition, not a primary (if that makes any difference)

Any thoughts...
Thanks in advance,
McRae

---

### Post by encompass on 2006-11-16
What is the output of fdisk -l/dev/yourdrive
for example... mine is...
> jason@tabby:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6374    51199123+  83  Linux
/dev/hda2            6375        6527     1228972+  82  Linux swap / Solaris
/dev/hda3            6528       10421    31278555   83  Linux
/dev/hda4           10422       36481   209326950   83  Linux
jason@tabby:~$ 
This will tell us if you have that 10 gig free

---

### Post by encompass on 2006-11-16
IT could be that root has to be on a primary partition... but I doubt it... that would be we could only have 4 OS systems installed.

---

### Post by mcraehutch on 2006-11-16
Encompass,
Thanks for the quick reply:)
when I initially did this the machine recognized my partitions using cfdisk. It shows the correct partitions.

Does that answer your question or does fdisk give you something more? 

Thanks Again,
McRae

---

### Post by mcraehutch on 2006-11-16
Encompass,
Just in case - here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    5  Extended
/dev/sda2            2676       13374    85939717+  83  Linux
/dev/sda5   *           1        2432    19534977   83  Linux
/dev/sda6            2433        2675     1951866   82  Linux swap / Solaris
/dev/sda7           13375       14593     9791586   83  Linux
ubuntu@ubuntu:~$

---

### Post by encompass on 2006-11-16
I need to see it... sorry... makes me feel confident before moving forward.
For me it is required.

---

### Post by mcraehutch on 2006-11-16
OK, the fdisk out put is in the post above yours:)

---

### Post by encompass on 2006-11-16
IT should work for you... sda7 right?  well, sorry to bug you more but can you give some screeshots too? you can do that on the live cd by pressing the prt screen button

---

### Post by mcraehutch on 2006-11-16
Your not bugging me! I really appreciate the help.
Give me a sec and I'll post the screen shots of the installer
Thanks again,
McRae

---

### Post by mcraehutch on 2006-11-16
EDIT: I got it - see next post

hmmm
I've got the screenshot but I'm not sure how to post it. I've never posted a pic on a forum - not too savy with this.
I hate to ask you this but how do I post it? It's saved as a  png file on the desk top - I assume a drag and drop will not do it;)

---

### Post by mcraehutch on 2006-11-16
file:///home/ubuntu/Desktop/Screenshot.png

---

### Post by mcraehutch on 2006-11-16
can you make that pic out Encompass? Once I enlarge it I can see it pretty well. Let me know.

Thanks again,
McRae

---

### Post by mcraehutch on 2006-11-16
I've got to get some sleep but I'll check tomorrow for any suggestions. Again, Encompass, thanks for your help - I appreciate your willingness:)

McRae

---

### Post by mcraehutch on 2006-11-17
bump
See screen shot. I tell it which partition to mount / on but it states "no root file system"

Any thoughts?

---

### Post by encompass on 2006-11-18
goto imageshack.com and then upload it there... place the link created in your new post.

---

### Post by rsambuca on 2006-11-18
There is definitely a bug with the Edgy installer not recognizing partitions being pre-setup.

I found a workaround:

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

