---
title: "Installing on MSI U100"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by jmedina on 2010-12-31
I've been using Windows XP on my netbook since I bought it a little over a year ago. I am considering using Ubuntu again. I am thinking about partitioning the Hard Drive so that Ubuntu has 50 GB. If I decide to get rid of Ubuntu, how would I repair the MBR without a restore disc? Thanks!

---

### Post by tommcd on 2010-12-31
There are various tools around the net that can create a WindowsXP recovery CD to fix the MBR:
[http://forums.pcpitstop.com/index.php?/topic/150212-boot-to-recovery-console-wo-xp-cd/](http://forums.pcpitstop.com/index.php?/topic/150212-boot-to-recovery-console-wo-xp-cd/)
[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html](http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html)
Note that I have not tried any of those, so I can not vouch for how well they work.
There are also other options like installing lilo, the Super Grub Disc, and Smart Boot Manager. See this thread:
[http://ubuntuforums.org/showthread.php?t=1134105](http://ubuntuforums.org/showthread.php?t=1134105)

Your netbook has been supported in Ubuntu for some time:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100)
Good luck! Write back if you need more help.

---

### Post by jmedina on 2011-01-01
Since I don't have a CD Drive because it's a netbook, is there a way I could use a flash drive or use another method to fix the MBR? I am new to partitioning - the times I used Ubuntu (Starting with Edgy), I would either install it on a second Hard Drive, or format the entire drive and install it. Thanks for your help!

---

### Post by jmedina on 2011-01-01
The last reply in this thread seems good.

[http://ubuntuforums.org/showthread.php?t=1617717](http://ubuntuforums.org/showthread.php?t=1617717)

---

### Post by tommcd on 2011-01-01
Yes, installiling lilo that way will fix the Windows MBR.
Here is a site that has detailed guides on dual booting Ubuntu and Windows:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by jmedina on 2011-01-01
Great! I knew that there was a way! Now I am really tempted on installing Ubuntu on it. I know it'd run a whole lot nicer. I found a partition tool for Windows and tried it last night. I was able to allocate 50 GB that I could use for Ubuntu. Should I make the partition using that or should I use partition tool on the installer?

---

### Post by tommcd on 2011-01-01
> **jmedina said:**
>  I found a partition tool for Windows and tried it last night. I was able to allocate 50 GB that I could use for Ubuntu. Should I make the partition using that or should I use partition tool on the installer?
Just leave the 50GB as unallocated space. Then boot from the Ubuntu live CD and use Ubuntu's partition tool to create the partitions you want for Ubuntu.

---

### Post by jmedina on 2011-01-01
Okay. I will try and do it today if I have time. I think 50 GB should be enough room. I already have the 10.10 bootable USB drive , so I don't even have to download it. Thanks again for your help!

---

### Post by jmedina on 2011-01-01
Help! I just setup the partition and selected it in Ubuntu - it prompted me to setup swap space, but I accidentally clicked proceed, what should I do?:confused:

---

### Post by jmedina on 2011-01-02
I created a 768 MB swap file that appears to be working good. Overall, it feels great to be using Ubuntu again!

---

### Post by jmedina on 2011-01-02
Well... It looks like having a swap file won't allow me to suspend. I get a swap header not found error. It allows me to suspend, however when I boot it back up I see the swap error again.

Also, if I unplug my computer when it's fully charge, it says it isn't and warns me that it will hibernate. What is going on?

Any help would be greatly appreciated.

---

### Post by jmedina on 2011-01-02
The battery problem appears that it appears to be a issue with the MSI U100 and Ubuntu. I used these steps from this thread and it provided a nice work around.
[http://georgia.ubuntuforums.org/showthread.php?t=1466327&page=3](http://georgia.ubuntuforums.org/showthread.php?t=1466327&page=3)

Also, for the moment I removed the swap file. I will probably readd it tomorrow since I determined that it wasn't causing the battery issue.

---

### Post by tommcd on 2011-01-02
> **jmedina said:**
> Well... It looks like having a swap file won't allow me to suspend. I get a swap header not found error. It allows me to suspend, however when I boot it back up I see the swap error again.
If you want to be able use suspend to RAM or use hibernation, you should create a swap partition that is at least as big as how much memory you have.
> **jmedina said:**
> 
Also, if I unplug my computer when it's fully charge, it says it isn't and warns me that it will hibernate. What is going on? ... The battery problem appears that it appears to be a issue with the MSI U100 and Ubuntu. I used these steps from this thread and it provided a nice work around.

I assume you got this fixed as per your post #12 in this thread above this one.
Since you have just installed Ubuntu, and if you really want to be able to suspend to RAM, then just reinstall Ubuntu again. Choose manual partitioning. Ideally, you should create 3 partitions:
1. root (10GB is plenty for root). This is where the Ubuntu operating system lives.
2. swap (1-2X the amount of memory you have *if you want to use hibernation*) You know what swap is for already!
3. home (the rest of the hard drive). This is where your data and user specific settings are stored.
Having a separate home partition is not mandatory, but it makes reinstalling Ubuntu easier since all your data is on a separate home partition.

You have made excellent progress so far! It took me months to figure this stuff out when I first installed Ubuntu!

Sorry I took so long to get back. I work 12 hour night shifts on the weekends ... even on New years Day :(

---

### Post by jmedina on 2011-01-02
Thanks tommcd! It's installing right now! I sized down the current partition for /home, and made /root 10 GB, which ended up being 9999 MB, and I made the swap a little over 4 GB. I only have 1 GB of RAM at the present time, but I am planning on adding another GB in a month, so I might as well plan ahead. I'll let you know how it goes.

---

### Post by jmedina on 2011-01-02
I reinstalled and it looks like everything's great! Thanks for convincing me to reinstall - it will end up being better in the long run. I will post back if I have any more questions, but it seems like it's working great - so much faster than XP:) Thanks again! I think the last time I used Ubuntu was about two years ago on a 700 Mhz box. It runs a lot more efficiently on my netbook.

---

