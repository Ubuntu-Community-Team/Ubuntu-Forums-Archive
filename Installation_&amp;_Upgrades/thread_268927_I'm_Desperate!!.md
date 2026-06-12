---
title: "I'm Desperate!!"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by pentium on 2006-09-30
Earlier today I was having a problem installing ubuntu off the live cd you get through shipit. I was told that the alternate cd will work and after a day downloading corrupt .iso's and searching for the torrent, I finally made a copy of the alternate cd. I popped it in and followed the instructions and hoped for the best. I come back after dinner to the install locked up *again*! I know it was not a drive problem. The drive had no partitions on it at all. I can rule out hardware because i had it hang with everything non-essential removed. I know it's not a temperateure problem also.
I also have to be careful when I use the live cd because when the screen saver turns on, yep, that locks the system too.
is there some special install method for the Dell Dimension 4100 or is ubuntu just trying to make me more unglued than I already am?

---

### Post by kamazu on 2006-10-01
Hi pentium,

try to explain your environment and the error a little bit more in detail, maybe it will give a clue what might have gone wrong...

cheer up!

---

### Post by pentium on 2006-10-01
I'll list the thre ways I have found the system will lock with:

-If you use the live cd you get through shipit:
I run install and go through the steps. The installation runs fine until I reach the 90% area. Once here the system will inetivably lockup at "looking for devices" or something like that. It locked here when I had gutted the system too. I presume a chipset goes kaput when ubuntu tries to load it.

-If you use the alternate cd install in OEM or text mode:
Do the regular input (name, password, clack etc.) at 50% or when the install mentions "installing python something" the system locks up.

-if you use the live cd and let the screensaver activate:
the screensaver comes on and suddenly the system is locked tighter than fort knox

I have noted two things:

-sound in and out still runs on live when the system has locked.

-If you reset the system and remove the cd after you try a live cd install (the one that crashes around 90%). Ubuntu loads but is unable to run update manager and the install option still exists

Currently the dell has installed:
-Leadtek 32 mb agp video card (nvidia chipset)
-aceex pci 56k modem
-wintv video capture card (it's PAL, Canada uses NTSC)
-dvd-rom drive (master, secondary)
-fast cd-rw (slave, secondary)
-5.2 gig hard drive for ubuntu
-384 mb pc133 sdram
-pentium III at 1 ghz
-QIC-80 250 mb tape drive (connect to floppy ribbon cable)

I heard somewhere there is a constant problem with nvidia video cards on ubuntu. is that true?

---

### Post by confused57 on 2006-10-01
Actually, Nvidia video cards are pretty well supported in Ubuntu.
You might try installing with your tape drive disconnected...if it works, you can reconnect after installing if the install is successful.
Only other thing I can see that "might" cause a problem is your wintv video capture card, I don't really know for sure.

---

### Post by tommcd on 2006-10-01
As Confused said, try installing without the tape drive. Also disconnect or remove the wintv video capture card, and the 56k modem (I assume you are on broadband?). I don't know if this will be successful, but at least you can rule out that these devices are causing the problem. The rest of your hardware should be ok.
With the alternate CD, did you verify the md5sums? Also you should burn the CD at the slowest possible speed. This will rule out a bad CD as the source of the problem.
For md5sum how to:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)
For md5sum from windows, get this:
[http://www.openoffice.org/dev_docs/using_md5sums.html#win](http://www.openoffice.org/dev_docs/using_md5sums.html#win)
THis will verify that the iso you downloaded is good, you will need to get the md5sum for the iso you downloaded:
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)
It's at the bottom of that page.

---

### Post by Ciego on 2006-10-01
I had what sounds to be a similar problem.  I found out(after about 3 nights of trying to install) that I had two different brands of RAM (also two different sizes) installed and Ubuntu really did not like it at all.  I took out one of the stcks and everything worked fine.  It looks like you may have two sticks that are different sized also  .... I would just give it a try with only one stick in there.

---

### Post by pentium on 2006-10-01
okay, so I will do the fllowing:

-remove tuner card
-remove modem
-remove 128 mb stick and leave 256 mb stick
-disconnect tape drive
-use alternate install cd and install in text mode.

I have checked the cd, it is ok also.

---

### Post by pentium on 2006-10-01
AAARG!:mad: 

I get to 97% (cleaning up) and the system just locks up. This is the closest yet I have gotten to finishing too!
Even if I restart, GRUB just gives error 15.

---

### Post by pentium on 2006-10-01
***THREAD CLOSED****
It turns out that it was a lack of ventilation and a poorly mounted heatsink. After remounting the heatsink and replacing a failed fan, install completed flawlessly and not I have what I want...I fast ununtu box:mrgreen: :mrgreen: :mrgreen: 

Thanks.

---

