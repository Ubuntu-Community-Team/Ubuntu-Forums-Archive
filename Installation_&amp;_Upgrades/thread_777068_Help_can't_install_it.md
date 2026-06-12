---
title: "Help: can't install it"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Telius on 2008-05-01
Hi guys,

I'm a noob with ubuntu and never used linux...

I'd like to have my first steps in this world but I have been trying to install ubuntu desktop for some days without success.

I first tried with the cd installation but even if the cd live ubuntu works fine (ubuntu seems to works fine in live mod), when I try to install it I get the errn5 (input/output error) always at 22% (when it starts copying files). 

Tried defragmenting the hd and burning new cds (3 attempts) at low speed but it failed.

Then I passed to install ubuntu from an image on the harddrive (from windows) as the guide "Installation/FromWindows" says. But again no success, since after pressing "ubuntu" for the second time it starts but says "error 17" "file not found".

I tried also with a usb memory but when the bios starts it says it's not a bootable partition (or something similar)

I could also use an external cd (firewire) or an external usb hd but I can't find something useful to install ubuntu from them to my internal hd.

My system has 512mb ram and I've got 1 partition with windows xp (10Gb) and about 60Gb unformatted on which I would like to install ubuntu.

Thank you for you support :)

---

### Post by Patb on 2008-05-01
Telius, this is only a partial reply.  

I assume you are using the live CD.  I would try installing directly from the alternate CD.  You haven't mentioned partitioning the 60G unformatted space.  If you have not already done so, you will need to set up you linux partition(s) in that space.  Setting up your partitions is an early step in the install process.  I would make one extended partition of the whole 60G and create two new logical partitions within that, one of about 10G as your root partition and another up to 50G as your home partition.  (Alternatively, you might want to make the home partition smaller and leave some space for another partition later, easily accessible from both Windows and Linux).  You will need to choose "Format" for the root and home partitions.  The partitioning step in the alternate CD install is quite logical and includes formatting options.  If you need, run through it a few times without committing at the "Write changes to disk?" step.  I always use manual rather than guided partitioning because I like to be in complete control of this.  

> **Telius said:**
> Tried defragmenting the hd ...
Defragmenting will only affect the Windows partition and you want to install on the other space.  It will thus be of no help for the actual installation, only for installation of whatever file Ubuntu needs to put on your Windows partions (I've never done that).  

Also, I trust you have used the "Check CD" option before trying to use the CD (even though it seems to work okay as a live CD).  I never try to use a Ubuntu installation disk before checking.  

I hope this helps.  

Cheers, Pat

---

### Post by Telius on 2008-05-01
> **Patb said:**
> Telius, this is only a partial reply.  

I assume you are using the live CD.  I would try installing directly from the alternative CD.  You haven't mentioned partitioning the 60G unformatted space.  If you have not already done so, you will need to set up you linux partition(s) in that space.  Setting up your partitions is an early step in the install process.  I would make one extended partition of the whole 60G and create two new logical partitions within that, one of about 10G as your root partition and another up to 50G as your home partition.  (Alternatively, you might want to make the home partition smaller and leave some space for another partition later, easily accessible from both Windows and Linux).  You will need to choose "Format" for the root and home partitions.  The partitioning step in the alternative CD install is quite logical and includes formatting options.  If you need, run through it a few times without committing at the "Write changes to disk?" step.  I always use manual rather than guided partitioning because I like to be in complete control of this.  


Defragmenting will only affect the Windows partition and you want to install on the other space.  It will thus be of no help for the actual installation, only for installation of whatever file Ubuntu needs to put on your Windows partions (I've never done that).  

Also, I trust you have used the "Check CD" option before trying to use the CD (even though it seems to work okay as a live CD).  I never try to use a Ubuntu installation disk before checking.  

I hope this helps.  

Cheers, Pat

Thx Pat; actually I tried partitioning a part of the free space available in 2 primary partitions: 1 of 1024 Mb swap, 1 ext3 of 10Gb with a mount point /. I did it during the installation process and it worked. It started, it formatted but when passed to copy the installation files, it blocked saying output/input error.

Maybe I am doing something wrong during the formatting process? I do I put 2 logical partitions in the new one? 

I tried defragmenting the ntfs because I read that with the installation from windows ("Installation/FromWindows") placing an image of the alternate cd in the primary root C, it's better having a defragmented hd.

In the meanwhile, I tried using grab4dos ("supplied" by the installation/fromWindows method) and he sees the (hd0,0) but he can find the file system I presume (error 17: file not found)

Yes, I checked the cds and it said they were ok.

---

### Post by Patb on 2008-05-01
Telius.  Thanks for the extra information.  There's not a lot more I can add.  (I completely forgot to mention about swap space).  

The partitioning seems fine as it is, although I would set up a separate partition for /home.  To confirm, could you post the output of "sudo fdisk -l" when you boot a live CD session.  

You can put two (or many) logical partitions within one extended partition.  But you are limited to not more than four primary partitions on each physical hard drive.   

Is there any impediment to trying an installation with the alternate CD?  Or have you already tried that?

Cheers, Pat.

---

### Post by Telius on 2008-05-01
> **Patb said:**
> Telius.  Thanks for the extra information.  There's not a lot more I can add.  (I completely forgot to mention about swap space).  

The partitioning seems fine as it is, although I would set up a separate partition for /home.  To confirm, could you post the output of "sudo fdisk -l" when you boot a live CD session.  

You can put two (or many) logical partitions within one extended partition.  But you are limited to not more than four primary partitions on each physical hard drive.   

Is there any impediment to trying an installation with the alternate CD?  Or have you already tried that?

Cheers, Pat.

Thank you again for your support mate :)

Since I was spending too much time on it, I tested one of my burned cds on another pc and... it worked fine: it installed ubuntu and now i'm testing it there. 

It seems like the other pc (an older one...) has got some problem; maybe I simply have to change the cd rom or worse... 

Anyway, since my aim is to have a small server on which I can share documents, look at my emails and get some documents when I'm out of office (can I look at my emails when I'm out like when I use outlook? I'm too noob, I know :(), and since I need it reliable, I think I'll buy a simple basic pc (300€) without a monitor and use it...

Suggestions? :)

Thx

---

### Post by Patb on 2008-05-01
> **Telius said:**
> Thank you again for your support mate :) 
You're welcome.
> **Telius said:**
> Can I look at my emails when I'm out like when I use outlook?
Almost certainly.  Check out the IMAP protocol.  I use that under Thunderbird email and like it.  If you get stuck, I would suggest starting a new thread under "General Help" or "Desktop Environments".  

I know next to nothing about servers.  Glad to see you're getting underway on the newer computer.  

Cheers, Pat.

---

