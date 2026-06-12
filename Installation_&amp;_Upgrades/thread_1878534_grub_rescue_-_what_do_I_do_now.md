---
title: "grub rescue - what do I do now?"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by liamhyland on 2011-11-09
Good Evening,
I had  dual booth system; Ubuntu 10.10 (I think, or was it 11.04) and ms xp.  When I switched the hard drive into another computer all I got was 'error: no such device: 27f............b. Grub Rescue.
Then I used the live Ubuntu CD and got the following:  It looks like in this picture that I do not have any Ubuntu installed!  I want to keep Windows but where do I mount the / point when I start gp parted. It keeps telling me that it does not have a root!  Any help will get this monkey off my back.  Thank you and Peace on Remembrance Day.

Liam in a pensive mood.

---

### Post by darkod on 2011-11-10
Yes, according to the pictures you do not have any linux partition on the disk. Not sure what happened exactly.

If you want to install ubuntu you need to shrink XP to make unallocated space. If you need instructions for this, ask first before you start because it's a bit tricky.

---

### Post by BillyBoa on 2011-11-10
> **liamhyland said:**
> Good Evening,
I had  dual booth system; Ubuntu 10.10 (I think, or was it 11.04) and ms xp.  When I switched the hard drive into another computer all I got was 'error: no such device: 27f............b. Grub Rescue.


Something is missing here. On this HDD it was not installed Ubuntu. There is no space to do it.

---

### Post by Gatemaze on 2011-11-10
Are there any other hard disks on this pc? Could you please on gparted go on top right corner and click on the menubutton that says /dev/sda and tell us what it says. If it is the sole disk then you have not installed ubuntu on this drive.

---

### Post by liamhyland on 2011-11-10
Good Morning, and thanks to your responses, and yes I am aware of there being only one partition.  Since I am at work I am unable to follow up with working on the desktop and in asking for requesting help in shrinking space.  Thank you all again and I should be back on the saddle re Grub and my desktop this evening.  In the meantime, have a great evening or morning or night...Liam from an overcast Sherwood Park.

---

### Post by darkod on 2011-11-10
The problem with XP is that:
1. It doesn't have a built in tool to resize partitions like win7 does.
2. It's a bit problematic if it doesn't do checkdisk after a resize.

So, unless you have a tool to shrink the partition under xp which are usually not free, you can do:
1. Boot with the ubuntu cd in live mode. Open Gparted.
2. Select the xp partition, and the resize option. Select to new size you want.
3. Click the green tick icon button in the Gparted toolbar. No changes are executed until you do this.
4. After the resize is done, reboot, let xp boot and in command prompt do
chkdsk c: /r
5. After checkdisk is done reboot xp few times just in case.
6. Once you are sure xp is fine boot again with the ubuntu cd and do the install.

---

### Post by liamhyland on 2011-11-10
Darkod, and company, I have that desktop running with live CD and it is in the process of re sizing the 147 GB hd to 47 GB with g parted...another 16 minutes to go...will keep you posted.  Thank you and may you have a great day, morning, and tomorrow is another new day with 11/11/11 to it...Liam

---

### Post by liamhyland on 2011-11-17
Darknod and other kind people,
Peace and joy.  I have fixed my partitions and hard drive.  Let me explain.  That hd was from another computer and the win xp in it was not able to be opened due to it going into a different computer (the xp licence agreement issue).  I then went and repartitioned the hard drive and put the ubuntu on it.  I had to make a small partition as it did not work the first time with a large partition.  So I was able to get into the files I had in that computer and save the information I had in the Ubuntu that was in it.  
Sometimes I think I know what I am doing and sometimes I do not know.  I also learned about changing power units and working from a sata drive to an ide computer set up.  Thanks to everyone and wish I could be of service to others too.  (By the way if you need some snow we have lots of it in the Edmonton area and more to come!!!) peace and joy from Liam

---

