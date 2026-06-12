---
title: "Ubuntu Server Install Problem"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by croker10 on 2010-10-15
Hi all;

I am trying to install Ubuntu Server 10.10.  I downloaded the files and made the image like the directions told me too, everything seems to go fine, up until I get to the point where it is "Installing base systems" It gets to 73% and stops.  This is the point where it is updating directory files or something like that.  I can't remember exactly what it says.  I figured I'd let it go for a little while, but after an hour, nothing happened.  This all happened twice.  

I have a system with an Intel Core 2 Duo that is 64 bit, 4 gigs of Ram and a 200 gig hard drive, so I know that I meet all the minimum criteria.

If any one has any ideas or has had this problem before, I would appreciate any advice or suggestions for resolution you may have.

Thanks!

---

### Post by mörgæs on 2010-10-15
Hi, welcome to the forum.

Have you tried the alternate installer?

---

### Post by SeijiSensei on 2010-10-16
Did you test to make sure the image wasn't corrupted?  See: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Bone Down on 2010-10-16
> **croker10 said:**
> Hi all;

I am trying to install Ubuntu Server 10.10.  I downloaded the files and made the image like the directions told me too, everything seems to go fine, up until I get to the point where it is "Installing base systems" It gets to 73% and stops.

Same issues here,  I am on my tenth attempt. I have found that if it hangs if I just leave the disk in and do ctrl/alt/del restart the install process the second or third attempt it will install.. 

third 10.10 download and cd creation
two 10.04 download and cd creation
fresh downloads each time and disk verified each time.

my latest attempt (select the same three install packages) dkpg is not working how frustrating...

---

### Post by Bone Down on 2010-10-16
I noticed that at 72-75% is the point where it is adding/updating the repositories. I did another clean install from scratch and on the first attempt today it went very smooth. It could just be that the repos were having some network issues or it could have even been my internet who knows.

dpkg is working as well and I now have webmin running so time to go see what I can break and fix this point forward.

cheers.

---

### Post by corcomp84 on 2010-10-20
> **Bone Down said:**
> I noticed that at 72-75% is the point where it is adding/updating the repositories. I did another clean install from scratch and on the first attempt today it went very smooth. It could just be that the repos were having some network issues or it could have even been my internet who knows.

dpkg is working as well and I now have webmin running so time to go see what I can break and fix this point forward.

cheers.


I am having the same problem, I am installing with the alternate CD ubuntu 10.10 with sata hard drives and a raid 0 system. it freezes at 73%.. I don't understand.. should I unplug the Ethernet cable?

---

### Post by corcomp84 on 2010-10-21
I solved my problem, it was a few issues, one my memory card was not seated very well, but I think the main problem was my CD rom-drive.. I changed drives and that fixed the problem perfect.. I installed a raid0 on two sata hard drives and even grub worked perfect.. I hope this helps others..

---

### Post by wildcrazyhorse on 2010-10-22
downloaded version 10.10 and created 2 different cd disk. Both will not install. Ran CD verify check on both of them and they failed. So, do I go back and re-download the 600 plus mb file again and try to re-burn another cd?  Also, I downloaded the desktop and get this. I have windows 7 on one machine and it installed quickly along side it as a dual boot os. both work okay. But I am trying to install the desktop on a standalone only operating system and it is hanging up and taking hours to install. what is the difference here. it seems to be taking forever on the retrieving files. I need to make sure it will work on my demo computer first....before I blow away my main computer windows, etc and install only ubuntu desktop.  I am scared here so I am waiting a couple hours to see what happens next. I will not be able to download the 32bit server version again until tonight starting at 2:00am. I have already reached my download daily limit. go figure. lol.  Could someone please help walk me through this and hold my hand... unix is not new to me and I am a good engineer, but disabled now. Am I doing the correct troubleshooting steps? and why is it taking forever on the stand alone desktop system when the side by side windows worked fast and easy.  Also, I tried the server install on 3 different computers and all of them have different cd drives. so hardware is not an issue, don't believe it is at least. thanks for your advice and help. I AM SOLD ON UBUNTU 10.10  Can't wait to see what the server has to offer and hopefully the desktop will install on it too...i have read documentation that tells me how to get the desktop server working..... what all does the server have built into it?
WildCrazyHorse:guitar:

---

### Post by mörgæs on 2010-10-22
Hi, welcome to the forum. 

A lot of questions... let's focus on them one by one.

As I wrote earlier: Have you tried the alternate version?
How strong is the machine on which you are installing, in particular how much memory does it have?

Some more advice on installing to get you started:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by shram43 on 2010-11-02
The same problem. 3-rd instllation is complete

---

### Post by guenzbub on 2010-11-20
Hello
Glad to give back some of the help I received from this forum:
A few days ago I read this post because I had the exact same problem. I then tried 10.04 server edition and tried to burn the CD from another (windows) computer. With the 10.04 Server version it asked my for a second CD, which of course does not exist, and with the other copies of the 10.10 I also stalled at 73 %. Then I read somewhere that it might be a problem of the CD-drive. So I got a USB-CD drive from a friend an tried the install again and in fact it worked. So this is the solution:
Install with a different CD-drive.

---

### Post by tbplayer on 2010-11-21
I have experienced this same issue - the installation stops at 73% when it is updating apt. I have tried both Kubuntu 10.10 and Ubuntu 10.10 alternative disks, and I tried both 32 and 64 bit versions - same results. In my research I read that someone had unplugged their network cable - I tried this but the installation still stalled. So I loaded Ubuntu 10.10 net install onto one of my jump drives and booted to the USB drive, and the installation set up normally. As others have suspected, it may be related to the DVD drive being used. I thought about testing with a different drive, but after finally getting Kubuntu installed after a few nights of hassling with it, I choose to finish the install rather than futz with it any further. ;)

---

### Post by WoraZ on 2011-01-01
I had that same problem. Tried reinstall few times with different options, but that  doesn't worked. Then i found that users have problems when they read CD  with NEC (I have it too) cd/dvd drives, so i changed it to TSCorp dvd drive and no hang  up on 73%. Perfect :)

---

