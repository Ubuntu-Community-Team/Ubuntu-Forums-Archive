---
title: "Installing Ubuntu with RAID 10"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by shelzmike on 2009-12-13
I will start out by saying a couple of things - first I may not have all the specifics here but will try to be as specific as possible. Also, I am not so new to Ubuntu but am far from a competent user per se with Ubuntu - but definately a beginner when it comes to RAID and RAID with Linux.

So here is the situation - we recently just did a complete overhaul on our network and upgraded to two large servers running Windows Server 2008. We are also in the middle of creating a complete new custom application and database using MySQL, Apache, Tomcat, and Java. For performance (and cost) on the latter, the database guy wants to use Ubuntu on the old server that was just decommissioned to run this DB and app. The catch is that he knows nothing about it and since I have had experience with it I decided to go for it. 

The server is several years old, but I think it will work fairly well for what we need it to do. 

It has an Itanium proc, 4GB and has hardware RAID (I think RAID 1 - this was set up before I was in the IT position here which has been just over a month).

I am interested in installing Ubuntu on this server using RAID 10 and I am guessing that my only option (based on research) is a software RAID, which is fine with me - the problem is that I am not quite sure how to accomplish this. 

I have seen a tuturial that seems to be pretty good here [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

However, I do get lost in places here. My one problem is that for some reason I cannot get the install to recognize all 4 of my drives. I have 3 that are 120GB and 1 that BIOS says is 260GB. 

The first thing I did was go into the BIOS and change SATA from RAID to IDE. However, UBUNTU install still seems to be reading only the 260GB drive. 

Any help on how to get to the point where I can use the above tutorial would be great. 

BTW - I am using Karmic Koala version.

Thanks!

Mike

---

### Post by Fcon_Vpro on 2009-12-13
I could be wrong on the following cos the ubuntu installer should pick up the drives but the following is just a shot in the dark.
You havent specified exactly which point you get stuck at.

What I would recommend is booting off the live cd, installing gparted, and seeing if gparted picks up the drives and from there you can initialise them instead of using cfdisk.

Follow step1 of this mdadm tutorial to initialise the drives: [http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

---

### Post by shelzmike on 2009-12-13
Thanks for the reply. Actually, when I went back to review the tutorial I pasted earlier I realzied that I might have spoken too soon. I was a little confused when doing it at first and didn't catch the fact that you partition each disk separately one at a time. I never made it past the sda part. I will try again tomorrow and partition sda, the sdb, sdc, etc. I thought I had opened gparted and it was only showing the one drive, but I may be confused. I will report back tomorrow on what happens. 

Mike

---

