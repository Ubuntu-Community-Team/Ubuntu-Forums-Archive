---
title: "What FS for RAID5 array + other questions"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Ellhound on 2010-01-21
I'm going to be running a software RAID5 array of 3 2TB disks soon, and if everything works I will add 3 more disks to it in a few weeks.

I'm trying to figure out what filesystem to use.

I remember reading about problems with Karmic, ext4 and large files, but I cant find the source anymore. Has this been fixed? 

If not, what filesystem would you suggest? 

I intend use a USB drive (Corsair flash voyager mini 4GB) for /, and the RAID5 array for /home and swap

Also any tips would be appreciated as this will be my first venture into linux software raid, and raid5 in general. 


Hardware:
Asus P5Q-E
E7200
2GB ram
3x 1TB HD
1x 1.5TB HD
3x 2TB HD (RAID5)

Thanks in advance.

---

### Post by tgalati4 on 2010-01-21
I don't expect the flash drive to last very long if you are using it for your root partition.  

Add up the energy costs of running all of those drives 24/7.  You might be surprised.

How do you plan on using the machine?  Editing video 8 hours/day?  Drafting and mechanical design?  Weather prediction and scientific number crunching?  Running a financial transaction website (like selling airline tickets)? 

If the answer is no to the above, then what benefits do you expect from RAID?

---

### Post by azagaros on 2010-01-21
Ellhound,

Google tested ext4 for reliability and found it to as good xfs.  I have personally had issues with the file system though.  It Doesn't like to be interrupted or forcibly stopped. It will destroy a superblock someplace and prevent the system from rebooting.  I don't know if there is a repair tool out there to fix the superblock the research I have done into the file systems like it say it should be recoverable to that end, but a SuperBlock is a inode of the ext line of file systems.  Sorry if I got a little detailed there I am reading and researching OS development, in the non Linux/unix world.  Thank god openWatcom got released, it just needs to get 64bit code generation and we will be set.

I hope that helps.

---

### Post by Ellhound on 2010-01-22
I'm well aware of the energy costs. I've been running a box with 6+ hard drives for years. 

I will be using this mostly as a file server, the reason I'm switching to RAID5 is simply so I dont lose any data when a hard drive fails. 

I found a page on the bug I mentioned earlier:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579)

Looks to me like it hasnt been fixed, so ext4 isnt an option right now.

---

