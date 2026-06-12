---
title: "Messed up HD during install &amp; can't recover"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by getagrip on 2008-08-10
I have 2 machines, a desk-top and a lap-top. I was able to install a WUBI version on my laptop and it works fine with XP as a dual OS.

I tried to do the same on my desk-top and its a nightmare.

Long story short I messed up the partitioning process during the install and I can't recover. 

When I boot linux from the CD and browse PLACES--> Computer ..I see a small partitioned portion of my HD as a separate file in the file browser window called "filesystem". I look into that file and see the boot folder ...but no **grub** sub-folder and hence no ..**menu.lst** boot file.

Which is why I believe my machine hangs up during the boot and displays **"GRUB LOADING STAGE 1.5".**. 

The problem is I can't get rid of this file. I reformatted my HD a billion times, but the reformat procedure won't touch that portion of the drive. I have wiped XP off my system in the process and cannot re-install it because this corrupt portion somehow cause the system to terminate during the installation attempts.

When I boot linux from the CD I can see the file ...but in that mode I can't delete it because the system prohibits that in the CD boot mode.

OK when I try to re-install linux, I use the manual-mode to partition the HD. That portion of the drives shows up as "dev/sda" as the device, and there is no size associated with it. 

I believe this is a very small portion of the HD as the other portion in the drive...the free space.... has a size of the HD capacity.
But there is a delete button during the manual partition, it grays out however when I select this bad section of the partition. 

I tried to partition the remainder of the HD, and set it as primary to mount from DOS ..but I get a root directory error message.

Please help me somehow get rid of this messed up portion of my HD.

---

### Post by cdtech on 2008-08-10
Have you tried the live cd gparted?

---

### Post by getagrip on 2008-08-10
> **cdtech said:**
> Have you tried the live cd gparted?

Remember.....  I have no OS on my machine, can this work in a pure DOS environment?

Also I'm not sure if it would help if I tell you that I have no desire to put back XP on my system ..so I really don't need a partitioned HD. 

I've backed up all the files before I started this ...and I want to move to a full linux OS. Thats why I just want to delete this corrupt portion of my HD and do  full linux install.

---

### Post by cdtech on 2008-08-10
Yes, it will boot and run in a dos like environment. You can run the graphical mode once you boot into the gparted disc.

---

### Post by getagrip on 2008-08-10
could you walk me through the syntax to accomplish this in DOS? 

Also I did a little digging and found this blog:

[http://answers.yahoo.com/question/index?qid=20080728065748AASrDin](http://answers.yahoo.com/question/index?qid=20080728065748AASrDin)

stating that gparted does not work in dos. 


I think, gparted is a nice tool, but what would help me more than anything else is someone with some DOS expertise ...because all I want to do is get rid of this partion on my HD and start over.

Thanks

I

---

