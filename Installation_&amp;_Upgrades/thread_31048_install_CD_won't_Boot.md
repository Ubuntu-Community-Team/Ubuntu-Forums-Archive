---
title: "install CD won't Boot"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by Juri on 2005-05-01
Hello, I am alittle new to ubunto, so sorry if I say anything stupid.  The AMD64 install cd will not boot.  It acts like any non-boot cd, it just gets skipped.  I am fairly certain its not my computer, as I burned the install cd twice, neither worked, and then burned the warty AMD64 install disk, that sorta worked.  Warty just word not reconize the hard drive I wanted to put Ubuntu on.  I have two hard drives one goes thru a SATARaid controller , thats the one ubuntu reconizes and the one I happen to keep windows on, the other says something about GIGAraid at boot up (theres more if need be I will reboot my computer w/ pen and paper in hand).  In my systems menu there is a  ITE IT8212 ATA RAID Controller, that might be it.
 
Thanks for your help

---

### Post by sethmahoney on 2005-05-01
I don't have an answer for you, but generally the more information the better, so if you can give us anything more to work with.  But just to make sure of what's going on, I have a question for you:

You're saying that at least sometimes the CD boots, right?  You can get into setup, but it fails to recognize your HD?  Or does the CD boot, start to load, but then setup fails to start?  Or does the CD not boot at all?

---

### Post by Juri on 2005-05-01
No, sorry for the confusion, the 5.04 cd never boots at all. However the 4.10 cd always does, it just never finds the hd I want it to. (I shouldn't use terms like always and never, as just maybe, I am one boot away from getting something to work, it just seems pretty consistant right now.)
 
On to more information:
As to the first problem, the 5.04 cd will not boot; its the AMD64 5.04 install cd burned form the iso from the United States official site. I have an AMD Athlon 64 processor 3200+, and a Gigabyte K8N Pro Mobo.
 
The next problem, the 4.10 cd will not find the hard drive, its a Barracuda ST340014A controlled by a ITE IT8212 ATA RAID Controller and something called GigaRAID RaidMGR version 1.3.1.5 ( 2003.02.18 ) Copyright 2003 Integrated Technology Express, Inc.
 
I can't think of any other relivent info. I know that the 4.10 cd problem may not belong here. But then I have no way of knowing if the 5.04 cd, if it would boot, has the same problem. Thank you for all your help

---

### Post by Juri on 2005-05-01
Something I forgot to add, that may or may not be important. While the smart boot manager (there is a link to it on [http://www.ubuntulinux.org/wiki/SmartBootManagerHowto]("http://www.ubuntulinux.org/wiki/SmartBootManagerHowto")) seems to work, it also does not load the 5.04 cd.

---

### Post by sethmahoney on 2005-05-01
I don't know if this is what's going on with you, but I had the same problem with a 5.04 CD.  I downloaded the ISO again and burned a new CD, and it worked fine.

So, next questions, I guess:

Is Windows is recognizing the Barracuda drive?

Is it a brand new drive, or something you already had installed?

---

### Post by Juri on 2005-05-01
Windows is recongnizing the drive just fine, as for the drive in question, I built my computer so by that standard the drive is at least 2 years old (most likely older as I didn't use top of the line parts)
 
I will try downloading the iso again, and go out to buy some more CD-Rs (as Ubuntu took my last ones O:) )
 
Thank you for responding.

---

### Post by Juri on 2005-05-01
I re-downloaded the 5.04 cd again and the good news is now it boots, the bad news is it has the exact same problem as the 4.10 disc.  The install cd won't find the hard drive I want to install it to.  Could there be a way to replace the the IT8212 controller with something that works?

---

### Post by Juri on 2005-05-01
interestingly enough there seems to be a linux driver for the IT2812 RAID controller I have been having trouble with, at  [http://www.ite.com.tw/software_download/software_download2.asp]("http://www.ite.com.tw/software_download/software_download2.asp") 

This link will download the driver
[[color=#800080]Binary and Source code[/color]]("http://www.ite.com.tw/product_info/file/pc/LinuxDriver_it8212_092005-09.zip")
of course the question becomes -- how do I add support to a OS I don't have yet?  hmm, maybe if I add the binary somewhere on the cd.  But Where?  Well I will keep trying,  and update my progress as I go.  Thanks for helping.  Later

---

### Post by Juri on 2005-05-01
It so happens that with the linux driver comes insturtions on how to install the driver durring the install of a linux distro, the problem is that the instructions don't expain how to do this with Ubuntu.  
 
I think I am pretty close, I all need to know is how to add a modual to ubuntu, like the cd does during the install, just I need to know how to do it from a floppy.
 
I already know how to mount the floppy and how to get into a shell from the install,  its just installing the linux driver part that I don't yet know how to do
 
Thanks for all you help

---

### Post by sethmahoney on 2005-05-01
If it has instructions for Debian, these will probably work for Ubuntu, too.

---

### Post by Juri on 2005-05-02
It has a folder for Debian, but no instructions for it.  I used the folder to create the disk, and then tried to follow the mandrake insturctions, as it takes more work in mandrake then in any of the other instuction: Redhat, turbolinux and suse.

---

### Post by sethmahoney on 2005-05-02
Did that work for you?

---

### Post by Craig Gilman on 2005-05-04
try smart boot manager - it worked for me !
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)

---

### Post by Juri on 2005-05-13
I solved the problem (sorta).  I went out and bought a new hard drive.  Although, I am running into new ones.  [http://ubuntuforums.org/showthread.php?t=34136]("http://ubuntuforums.org/showthread.php?t=34136")Thanks for all your help

---

