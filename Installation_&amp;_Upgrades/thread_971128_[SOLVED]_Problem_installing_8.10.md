---
title: "[SOLVED] Problem installing 8.10"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by alexeix on 2008-11-04
Hi,

I'm having big problems trying to do a fresh install of 8.10 and I'm hoping for some advice.

Firstly, I have a separate HDD with Mythbuntu and I was able to upgrade that at the weekend without any issues (from Hardy to Intrepid), via Synaptic Package Manager.

However, when I attempted to burn a CD with 8.10, I straightaway started having issues.  I tried 32bit images from 2 different sources (on the Ubuntu web site), but when I tried to burn either one in Brasero, I kept getting failed burns and ruined CDs.
Eventually I gave up and used my Vista laptop to burn one of the images - worked first time, no problems.  

I then tried to install 8.10 on the original machine on a brand new 500GB HDD.
I was asked to enter my user name, select keyboard configuration, etc., but after selecting the partition details and kicking off the process, I got the following error a few minutes later (around the 5% mark): 
"Installation failed.  The installer encountered an error copying files to the hard disk. [Errno 5] Input/Output error.
This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk..."

So, I changed my DVD drive for an old CD/RW drive, but got the same error.

I was booted into the Live CD after the installation stopped, so I created a bootable USB key with 8.10, however, when running that, the installation ended at the same point!

At this point, I feel my hard drive must be faulty (although since it's a replacement of a previously faulty drive, I think I'd be unlucky!), or 8.10 doesn't like my hardware - OR is there some more obscure possible reason?).

I will try installing Hardy and if that works, I know my hard drive is fine.  I did run a quick diagnostic check last night, with no problems detected, but may need to run a full surface scan.

Failing that as the cause, are there any other suggestions?
Thanks in advance.

---

### Post by cariboo on 2008-11-04
If the installation is failing at the same point from different install media, that should tell you something is not right. Have you tried any of tha noapic options you get when you press F6 at the installation menu?

Jim

---

### Post by alexeix on 2008-11-04
Yeah, but at first, I just kept thinking there might be something wrong with the image I downloaded.
It's a brand new replacement HDD, so of course, I thought it was unlikely to be duff.  Now, I think it's the most likely option...

Haven't tried the options you suggest, but will do.
Thanks.

---

### Post by dci-Japan on 2008-11-05
Installing Ubuntu 8.10 [Errno 5] My Success Story

My solution to [Errno 5] on Ubuntu install was to remove some RAM modules.

I had great trouble installing 8.10 to my computer (model: HP d330). It took me three days and countless hours researching around the internet. Here is my success story.

I downloaded the ISO and attempted to install from the Live CD. The following error appeared at about 24% of install process:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

1. Attempted reburn CD-R at slower speed. Same error.
2. Attempted install with "Alternate CD". Same problem (it froze up somewhere in "copy files to disk" process).
3. Attempted boot from Live CD and double click "Install". NO GO. Wouldn't even start process.
4. Repeated all the above in various ways. Same results.
5. Tried changing the various choices under F6 on boot-up. Freeze or same error. 
6. Live CD then begin to hang on boot from CD. Couldn't get anything to do anything.
7. Attempted to install from Flash card (using separate PC to set it up). Booted fine, but same error on install.
8. Attempted many solutions offered on various forums online. Still no luck.
9. Tried noapic options and others to no avail.
10. Tried repartitioning hard drive, and wiping hard drive and etc. etc. etc.
11.Gave up and installed Windows XP. Hated it (as usual). Waited several hours. Kept repeating all the above plus anything I could think of. Redownload ISO. Burn at slower speeds. Try Alternate CD. Try Flash card again. NO LUCK. Fiddle with various settings again.

And then I used the little grey cells in my head (as Poirot would say in an Agatha Christie novel). I remembered someone somewhere suggested RAM error as the culprit. I ran the memory test without a problem (that took many hours!), but still I was supicious about the memory. My PC has four memory slots but with 3 actually memory sticks. 256Mb (original memory stick that came with computer) + 1Gb (cheap no brand stick added later) + 1GB (another added no brand stick). I simply took out the two 1Gb stick and left only the original 256Mb stick and attempted an install. Bang! It worked. No error. No problem (except it was as slow as molassis to install...). After the successful install, I replaced the 2Gb of memory and rebooted. Everything worked out. RAM modules might be faulty but everything seems fine.

I'm not sure if this solution will help everyone. The cause of [Errno 5] might be different for each machine, and sometimes just trying a million attempts leads to an eventual success. But in my case, removing most of the RAM solved the problem. 

Finally I can get on with enjoying Ubuntu 8.10.

---

### Post by alexeix on 2008-11-07
Well, I only have 2 memory slots in my Shuttle SN95G5v2, but I tried removing one unit.

When attempting to install Ubuntu 8.10, it seemed to get a little further, but then the same error occurred.

I'm going to scan the hard disk for problems and as a last resort, I may try installing Hardy and do an upgrade.
The question is, will an upgraded Ubuntu look exactly like a fresh 8.10 install?

It seems that this latest release may have some issues - I haven't had any similar problems with the previous ones.

---

### Post by alexeix on 2008-11-09
Groan...now Hardy won't install...gets to around 78% at the partitioning stage and then nothing else happens - the hard drive isn't being written to, but I can still move the cursor around.

I'm going to scan the hard disk for errors using the manufacturer's utility.

Any advice/suggestions in the meantime would be appreciated.

---

### Post by alexeix on 2008-11-09
I ran tests on the CD and some corrupt files were reported.

I then downloaded a fresh image direct from Canonical in the UK and this time, 8.10 installed correctly.

So I don't know if the problem was caused by the original image I used, the physical CD, the burning process or something else. 

Regardless, it's finally working...

---

### Post by electronic spark on 2009-08-06
I got the installation of ubuntu done by removing one of two 256mb memory module.  I have not had the same problem with another distro like Greenie, but with ubuntu 8.10,9.04 and with Mint 6 & 7
I did the install from USB memory stick.
What is the fix??

---

