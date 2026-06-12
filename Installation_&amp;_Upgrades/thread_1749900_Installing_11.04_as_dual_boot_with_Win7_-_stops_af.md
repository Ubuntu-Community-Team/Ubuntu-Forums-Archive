---
title: "Installing 11.04 as dual boot with Win7 - stops after setting partition size"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by OffsideInVancouver on 2011-05-05
Hi, 

  This is my first time trying to use / install a Linux distribution.  I have Windows 7 on my laptop and am attempting to install Ubuntu 11.04 from CD.

 I boot from the disk drive, follow the prompts and eventually get to the screen where I can set how much space I want to give to the Ubuntu partition vs the Windows partition.  My hard disk is 250GB, so I reduce the Windows one to 100GB (currently has 80GB of files on it) and set the Ubuntu one to 130GB (the other 20GB is split between the two hidden Windows 7 partitions).

 I then click to continue and the progress bar for the install starts up but doesn't move, it just sits at 0%.  I realised that the dialogue box underneath the progress bar can still be expanded and asks me to test using -n and -s, but when I type either of these into the box and hit return, nothing happens. 

I have checked my download of the .iso I used using WinMD5Sum and the hash matches up.  I have already tried installing from USB but this threw an error, hence using CD. 

My laptop is a Dell Inspiron 1546 running Win 7 Home Premium 64 bit 
Processor: AMD Turion X2 Dual-Core Mobile RM-75 2.20GHz    

Has anyone come across a similar problem?   

Please let me know if you need any more info.   

Many Thanks,   

OiV

---

### Post by ssican on 2011-05-05
Maybe this two guides of the "Illustrated Dual Boot Site" can help:
1)Graphical Installation 'C'. 

- Windows and Ubuntu installed dual boot in the same hard disk 
- partition the hard disk first _**using Gnome Partition Editor in the Live CD**._ [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

2)Graphical Installation 'B'.

- Windows and Ubuntu installed dual boot in the same hard disk
- _**use the Ubuntu Live CD's installer's in built partitioner for 'Manual Partitioning' during the installation**_.
 [http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

---

### Post by Sun_Coaster on 2011-05-05
Not quite on topic, as your issue is with partition sizes,
but you can create a dual boot system with Wubi.

Can you partition from within Windows first ?
Create a D: drive for data.

I've just installed 11.04 on a Windows 7 netbook - (EEE 1008H 1GB ram.)
I used wubi from Ubuntu.com, executed it in windows and it installed smoothly.
No need to worry about partitions, ubuntu installs on C: and I can use D: for data.

I can now dual boot either win 7 or ubuntu, and both can see and use D: for data.
See [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

.

---

### Post by OffsideInVancouver on 2011-05-06
Hi,

Thank you both for your feedback.  I decided to go with the WUBI option for now to get up and running as quickly as possible.  I think it works (might be something wrong I haven't noticed yet), but it is very slow to boot up.  When I turn on my laptop I get a dual boot option between Win 7 and Ubuntu, on choosing Ubuntu I then get taken to another screen to pick between Ubuntu, Ubuntu Recovery mode and something else.  On selecting Ubuntu I then get a plain black screen with a blinking cursor in the top left and it takes 50 seconds before I get to the Ubuntu log-on screen.  Should it take that long?  I was under the impression that it was really quick to boot in comparison to Windows but that seems about the same length of time, if not more.

Thanks,

OiV

---

### Post by wilee-nilee on 2011-05-06
> **OffsideInVancouver said:**
> Hi,

Thank you both for your feedback.  I decided to go with the WUBI option for now to get up and running as quickly as possible.  I think it works (might be something wrong I haven't noticed yet), but it is very slow to boot up.  When I turn on my laptop I get a dual boot option between Win 7 and Ubuntu, on choosing Ubuntu I then get taken to another screen to pick between Ubuntu, Ubuntu Recovery mode and something else.  On selecting Ubuntu I then get a plain black screen with a blinking cursor in the top left and it takes 50 seconds before I get to the Ubuntu log-on screen.  Should it take that long?  I was under the impression that it was really quick to boot in comparison to Windows but that seems about the same length of time, if not more.

Thanks,

OiV

Just so we are on the same page here wubi is a file in windows it has a psuedo virtual partiton, it is not a real dual boot so will run slower. Not bad just giving the highlights lol.

If you want to put it in a partition like you were trying originally at some point, ask for help if needed. You can actually move the wubi to a actual partition all by its proud self.

---

### Post by OffsideInVancouver on 2011-05-08
Cool, thanks for the tip :)  I think I'm going to spend a few months getting used to Ubuntu then I'll move it into a separate partition when I know what I'm doing.  Eventually I'm hoping to remove Windows from my laptop entirely and use my Windows 7 license on my old XP desktop.

---

