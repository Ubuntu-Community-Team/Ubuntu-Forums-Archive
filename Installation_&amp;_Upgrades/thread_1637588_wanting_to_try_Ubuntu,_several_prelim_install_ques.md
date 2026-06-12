---
title: "wanting to try Ubuntu, several prelim install questions"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by midcentgent on 2010-12-04
I just purchased a used laptop off of Craigslist (I know).  The sticker says Vista but there was a counterfeit Windows 7 running on it (I'm 99% sure it's not genuine).  Anyway, computer crashed, won't start, etc.  So.... this seems like a great time to think about Linux, because I have no excuses not to try right now.
I'm pretty sure the hard drive is fine, but I have no idea what partitions were made on the botched 7 install (I never looked and now it won't boot anyway).
Will a Ubuntu (or is it *an* Ubuntu?) install deal with the partitions?  I don't want Windows on my machine anymore, so I'd prefer Windows be eliminated altogether.  Or will I need Gparted or similar partitioning software?
How will I deal with drivers?  I never made a note of what drivers are on the machine.  It's a Dell Latitude E6400 and I could look on Dell's website for the drivers.
Thanks in advance.

---

### Post by AlphaLexman on 2010-12-04
Your best option is to download a 'live CD' and give the laptop a good test run without actually changing anything. I have bought two laptops off of craigslist (however carefully) and have had no problems whatsoever. But I did take a 'live CD' with me just to test them before I purchased them!

---

### Post by oldfred on 2010-12-04
Gparted is part of the liveCD. You can easily see what partitions are there, unless they are damaged and gparted often will not mount NTFS partitions that need chkdsk.

You should not need drivers and any windows drivers will not work. If you do not have hardware that the CD supports directly it will usually offer to download drivers, so ethernet connection is best while installing as wireless often is one of those that needs special drivers.

As AlphaLexman said, use liveCD to test. It will not be as fast as it is loading from the CD, but will let you know if you have any major issues and what to ask next.:)

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by ToFue on 2010-12-04
about the driver question: So does that mean that ndiswrapper no longer needs the windows driver anymore for the broadcom chipset?  It's been a few distros since I've had to worry about that, as my laptop's fully supported..

@ oldfred:
The advice of the others are best, using livecd. You can burn both the 32bit and 64bit livecd versions so you know what your laptop can handle even... or use what you have burned, run the liveCD, open a terminal and anylize:
```

$ sudo cat /proc/cpuinfo 

or 

$ sudo cat /proc/cpuinfo | grep "address sizes"

```
looking at the part that says "address sizes", you'll know what bit version your machine can handle..

Cheers, & welcome to freedom!

---

### Post by akand074 on 2010-12-04
The OP said he didn't want Windows on it anymore. Just put in the disk, you can try it out if you want but when you decide to install just choose to let Ubuntu use the whole disk. It will wipe your entire hard drive clean, format it, and install Ubuntu.

---

### Post by oldfred on 2010-12-05
akand074 is correct, but I like to add a partition or two.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. 

If just installing Ubuntu you can use all primary partitions. I still would put swap in an extended/logical so you have a primary left to use in case you ever wanted to add windows as it has to have a primary partition.

---

### Post by ToFue on 2010-12-29
> **akand074 said:**
> The OP said he didn't want Windows on it anymore. Just put in the disk, you can try it out if you want but when you decide to install just choose to let Ubuntu use the whole disk. It will wipe your entire hard drive clean, format it, and install Ubuntu.

@ akand074

That's completely NOT what I was referring to. I wasn't clear enough in my comment where I typo'd to Oldfred instead of Midcentgent. I understand that windows was intentioned to be abolished as stated by the original poster;

 What I was asking was the need for the windows driver to be used on linux for ndiswrapper - 'is that still in effect with current ubuntu releases or is that no longer an issue?' where you need the windows driver to make the wrapper driver work in linux for certain wireless NIC's. It was an attempt to put it out there in case the OP were to delete it before he can get a copy where it may be needed to establish a wireless connection in a new linux install where ethernet may not be available.

My intended comment was mis-represented. First I unspecifically addressed those who may be knowledgeable about the driver, where I was ignorant to the specific hardware compatibility but thought of a relevant exception. Then I attempted to address the OP where I fully endorsed the recommendations of the previous two posters. I'm sorry for the confusion.

To touch on my hibernate experience (my swap is less than total RAM for performance purpose) I have to be careful of how many apps and how large they are running so-as to not get 'out of swap' errors, and if needed reduce the amount of active processes like firefox tabs, files that I can call later, making todo notes, etc. by monitoring the memory sizes in system monitor before hibernating.

---

