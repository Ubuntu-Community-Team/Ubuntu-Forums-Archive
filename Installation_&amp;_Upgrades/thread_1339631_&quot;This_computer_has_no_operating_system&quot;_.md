---
title: "&quot;This computer has no operating system&quot; install msg"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by presence1960 on 2009-11-27
I have multiple hard disks like this:

sda is an ext 3 data partition 
sdb is backups & PING images
sdc1 is XP
sdc6 is Jaunty
sdc7 is Karmic
sdd is an external USB HDD with Jaunty Live USB on sdd1

When I boot the Live CD/USB I initially get the message "this computer has no operating system on it".

I happened to notice the drop down box under "use entire disk" was set to sda. (see first pic attached)
So I selected sdc and voila all my OSs were detected and showed up in the graph at the top. (see 2nd pic attached)
I think the detection of OSs and the graph output are dependent on which disk is selected in the drop down box under "use entire disk". I would suggest to select the disk your OSs are installed to in the drop down box under use entire disk.

Once I selected sdc and my OSs were detected and displayed in the graph I was still able to use all 3 options to install Ubuntu.

I am posting this because there are a lot of threads saying Ubuntu installer failed to detect their OSs at the partitioner window. I would say more than a few of these people have multiple hard disks with their OSs maybe installed on another disk than sda.

Here is my fdisk output to help visualize my setup:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85858585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00072abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59950   481548343+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02020202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdc2            5223       10444    41945715    5  Extended
/dev/sdc5            5223        5744     4192933+  82  Linux swap / Solaris
/dev/sdc6            5745        8094    18876343+  83  Linux
/dev/sdc7            8095       10444    18876343+  83  Linux

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079662

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         115      923706    b  W95 FAT32
/dev/sdd2             116        2073    15727635    7  HPFS/NTFS
/dev/sdd3            2074        9964    63384457+  83  Linux
ubuntu@ubuntu:~$ 
```

---

### Post by ajgreeny on 2009-11-27
Most people seem to miss the option to set their partitions manually, which is what is needed in this situation.  Once you have installed a few times it becomes second nature to you, and you will do it without thinking too hard about what you want, or need.  However, for a new user who has probably never installed an OS in their life, it will appear as a major task.

Quite how it can be improved for new users, I am not sure, but perhaps others have some ideas on this.

---

### Post by louieb on 2009-11-27
:guitar:Had not noticed that bit of misinformation. Thanks for pointing it out.  

> I would say more than a few of these people have multiple hard disks with their OSs maybe installed on another disk than sda.

The messages wording could probably be improved by replacing computer with hard drive.  

](*,)I was paranoid enough the 1st few times I set up a computer to dual boot.

---

### Post by presence1960 on 2009-11-27
> **ajgreeny said:**
> Most people seem to miss the option to set their partitions manually, which is what is needed in this situation.  Once you have installed a few times it becomes second nature to you, and you will do it without thinking too hard about what you want, or need.  However, for a new user who has probably never installed an OS in their life, it will appear as a major task.

Quite how it can be improved for new users, I am not sure, but perhaps others have some ideas on this.

I hear you AJ, I always do a manual installation. This thread was prompted by a disagreement on another thread between willee-nilee and myself. 

Since I always use the manual option I never noticed the top graph and the message that my computer has no Operating system installed. I just select manual and proceed with the installation. I thought of posting this though because I see a lot of threads relating to this where OPs say the partitioner window says they have no OS installed when in fact they actually do. I believe this is the reason that is happening.

---

### Post by presence1960 on 2009-11-27
> **louieb said:**
> :guitar:Had not noticed that bit of misinformation. Thanks for pointing it out.  



_***The messages wording could probably be improved by replacing computer with hard drive.  ***_

](*,)I was paranoid enough the 1st few times I set up a computer to dual boot.

Excellent idea there, louieb!

---

### Post by wilee-nilee on 2009-11-27
> **presence1960 said:**
> I hear you AJ, I always do a manual installation. This thread was prompted by a disagreement on another thread between willee-nilee and myself. 

Since I always use the manual option I never noticed the top graph and the message that my computer has no Operating system installed. I just select manual and proceed with the installation. I thought of posting this though because I see a lot of threads relating to this where OPs say the partitioner window says they have no OS installed when in fact they actually do. I believe this is the reason that is happening.

And I appreciate all your help no harm done. ;) I wasn't going to post until I saw a reference to me. the unallocated problem seems to be a reoccurring problem.

I didn't see it as a argument we were both correct in specific circumstances.

---

### Post by presence1960 on 2009-11-27
> **wilee-nilee said:**
> And I appreciate all your help no harm done. ;) I wasn't going to post until I saw a reference to me. the unallocated problem seems to be a reoccurring problem.

I didn't see it as a argument we were both correct in specific circumstances.

I did not say it was an argument, my exact words were a disagreement!

And that is what we did, we disagreed with each other & no harm was done.

P.S. Just because we disagreed on that thread does not mean loss of respect for you.

---

### Post by wilee-nilee on 2009-11-27
> **presence1960 said:**
> I did not say it was an argument, my exact words were a disagreement!

And that is what we did, we disagreed with each other & no harm was done.

P.S. Just because we disagreed on that thread does not mean loss of respect for you.

Sorry I meant disagreement, and I feel the same I wanted to comment a thanks for this thread but I thought that letting it go was a better idea. ;) I am a enthusiast not a geek but am careful with helping others the best I can be. I think we all want to help others generally without any harm to their processes.

---

### Post by presence1960 on 2009-11-27
> **wilee-nilee said:**
> Sorry I meant disagreement, and I feel the same I wanted to comment a thanks for this thread but I thought that letting it go was a better idea. ;) I am a enthusiast not a geek but am careful with helping others the best I can be. I think we all want to help others generally without any harm to their processes.

A healthy exchange of ideas even during a disagreement helps all involved including the OP, as long as it doesn't become a personal attack. The OP gets to see different ideas and maybe try some or all of them. I believe we all learn from each other, although sometimes human nature creeps in there. but for the most part we all do a good job in here.

There was a benefit because of our discussion I booted my Live USB and noticed something I never have before that related to what a lot of people have been posting about: The message that the computer has no operating system when in fact it does. I never noticed it before because I always do manual installs and don't even look up top at that screen, I just click manual and proceed.

Now louieb has a good idea- that message "no operating system is installed to this computer" can be amended to replace computer with hard disk.

P.S. There is no disagreement great enough in my eyes to not like someone or not converse with someone in here.

---

### Post by nss0000 on 2009-11-28
Honestly ....

NO casual lusr sets his partitions manually. None who are still sane! Setting partitions is ONE reason he "hires" an OS. I mean, if the pros can't make a good default decision, then he's in deep water from-da-start. 

Hobbyists are different, as are IT professionals. The prudent casual lusr would no more partition manually than try running multiple OSs or flash his BIOS into brickland. 
Say nothing ... of a new 500-G sATA costing $80.

---

### Post by presence1960 on 2009-11-28
> **nss0000 said:**
> Honestly ....

NO casual lusr sets his partitions manually. None who are still sane! Setting partitions is ONE reason he "hires" an OS. I mean, if the pros can't make a good default decision, then he's in deep water from-da-start. 

Hobbyists are different, as are IT professionals. The prudent casual lusr would no more partition manually than try running multiple OSs or flash his BIOS into brickland. 
Say nothing ... of a new 500-G sATA costing $80.

This thread was meant for those you call casual user, not those who partition manually. I always partition manually and that is why I never noticed the message that my machine has no OS installed. I always just click manual and never look at the top of that window. maybe reread the first post and see what we are talking about. Then go back through the threads and see how many are baffled because the partitioner is reporting that they have no OS installed when in fact they do.

Am I insane? I don't know because I don't believe in those labels you use. I don't know where I would fall in- casual user, hobbiest? Definitetly not IT professional. Probably glad of that because my experience with help desks at work are that I solve more network/software/hardware issues than they do. Most of the district calls me first instead of the help desk. The help desk manager asked me to come work for them, but since I don't have my certs that can't happen.

---

### Post by presence1960 on 2009-11-28
> **nss0000 said:**
> Honestly ....

NO casual lusr sets his partitions manually. None who are still sane! Setting partitions is ONE reason he "hires" an OS. I mean, if the pros can't make a good default decision, then he's in deep water from-da-start. 

Hobbyists are different, as are IT professionals. The prudent casual lusr would no more partition manually than try running multiple OSs or flash his BIOS into brickland. 
Say nothing ... of a new 500-G sATA costing $80.

Don't sell people short. Categorizing people is never a beneficial thing. people are vibrant and are able to learn & grow, even experiment. Don't attempt to limit the unlimitless regardless of your perception of their ability or where they came from.

---

### Post by raymondh on 2009-11-28
This is good learnings presence .... thanks.

Am curious now.

Will try to experiment when I get home using a 9.10 liveUSB and a single-drive laptop.

---

