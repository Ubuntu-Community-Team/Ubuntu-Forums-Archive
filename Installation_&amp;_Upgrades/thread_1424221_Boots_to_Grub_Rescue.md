---
title: "Boots to Grub Rescue"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2010-03-07
**can't pass grub rescue** 			
 			 			 		   		 		 		I have been trying to fix a broken Ubuntu 9.10 system. I cannot get past the "grub rescue" when booting from the 9.10 CD
I do NOT care about data loss. I want to install Ubuntu as if a clean install.
I used systemrescue64. used Gparted and believe I wiped the hard drive. Under Gparted, the drive shows as one continuous partition of 584 GB with an 10 GB extended partition and a 10 GB swap file
When I attempted to format the drive as Ext 4, the system locked up. I rebooted to retry it again and it froze both times. I could not open the CD drive during this and had to reboot to open the Cd drive and remove the rescue64 Cd.
I scanned the forums and found that 9.10 includes Ext 4, so I tried booting to the Ubuntu 9.10 disc, but keep getting the "grub rescue" prompt but it keeps refusing any command as an "Unknown command."

How do I get this thing working with a functioning Karmic OS?

My System info:
AMD Phenom X4
Asus M3A78-EM motherboard with onboard ATI Radeon 3200
4 GB ram
Western Digital 640 GB HDD

I've been trying to get the system up for more than 2 weeks. I have read hundreds of forum posts, tutorials and everything else I can find, but every answered question brings more questions and another lengthy search. I just can't do it anymore.

PLEASE HELP
Thank you.

---

### Post by Barriehie on 2010-03-07
Using gparted delete the space on the drive and try again with the install CD, leaving the space unallocated.

HTH

---

### Post by mne9476 on 2010-03-08
I had the problem you describe regarding GRUB rescue. I have a working system now. Here's what I did which you may want to try since you don't care about losing data:

Downloaded a fresh copy of 9.10 and burned a CD.
During the install, I deleted all my partitions and created new ones (/boot, /, /usr, /home, and /swap)
Install finished correctly and system booted up just fine.

Some of the language packages "couldn't be deleted." I immediately ran Upgrade Manager. I was told "Not all the upgrades can be installed due to a previous error" or something to that effect. Using the broken filter, I was told that it was the language pack again!  I completely removed the package and rebooted. Booted up fine. Update Manager now reports no errors and says I am up-to-date.

I used file system type EXT3 this time -- hopefully the system won't crash as much as in 9.04 and the 9.10 I had earlier.

I lost all of my data and programs (/home and /usr) btw. The drive is too large to backup.

----------

I have to say that I am very dissatisfied with the quality of the Ubuntu distributions. With each release, I am expecting a better package than the previous, but that's not the case. Every time, it's a new set of problems.

---

### Post by Gnusboy on 2010-03-09
> **Barriehie said:**
> Using gparted delete the space on the drive and try again with the install CD, leaving the space unallocated.

HTH

Yeah, I did that 6 or 8 times now. I can't get the Live CD 9.10 to open, but I did get the Live Cd in 9.04 to boot. It will allow me into the try Ubu ..Now, but then it won't install.
If I try to redo the disk delete and repartition, when it starts to formant to EXT 3, EXT 4 - the whole system freezes at the 5% mark.
I've tried the whole process with different versions of Gparted and at least 3 versions of Ubuntu. All version were check summed and matched both before and after D/L and burn.
I even tried using the pkg manage to D/L Jaunty and Karmic - but no joy and it freezes. 
didn't try using the terminal yet.
As far as I can tell, my hardware is ok. Ran integrity check on the HDD and an overnight Memtest. Everything is fine.
I've used System-Rescue64 Ultimate Boot Disk, MHDD and the Live Cds. 
Honestly, I have no idea why this is such a bitch.
Thank for the suggestions. Keep 'em coming

---

### Post by Gnusboy on 2010-03-09
> **mne9476 said:**
> I had the problem you describe regarding GRUB rescue. I have a working system now. Here's what I did which you may want to try since you don't care about losing data:

Downloaded a fresh copy of 9.10 and burned a CD.
During the install, I deleted all my partitions and created new ones (/boot, /, /usr, /home, and /swap)
Install finished correctly and system booted up just fine.

Some of the language packages "couldn't be deleted." I immediately ran Upgrade Manager. I was told "Not all the upgrades can be installed due to a previous error" or something to that effect. Using the broken filter, I was told that it was the language pack again!  I completely removed the package and rebooted. Booted up fine. Update Manager now reports no errors and says I am up-to-date.

I used file system type EXT3 this time -- hopefully the system won't crash as much as in 9.04 and the 9.10 I had earlier.

I lost all of my data and programs (/home and /usr) btw. The drive is too large to backup.

----------

I have to say that I am very dissatisfied with the quality of the Ubuntu distributions. With each release, I am expecting a better package than the previous, but that's not the case. Every time, it's a new set of problems.

Mne
Thanks. See my reply below for details.

---

### Post by mne9476 on 2010-03-12
Hello ... I am back ;)

I took the suggestion of trying Debian 5,04 and used it for a day or so. I didn't notice it being any more stable than Ubuntu -- in fact, I got regular kernel faults.  It took about 5 tries to get Debian to install.

I went back to Ubuntu 9.10 -- took another few tries to get it installed, but now it's running and the only crash was Firefox after I installed Adobe Flash. I removed Firefox and Flash and reinstalled Firefox without Flash.

I am using pretty obsolete hardware which is probably the source of many of my "woes."  My specific problem this time turned out to be a corrupted MBR. I installed LILO with Debian because GRUB kept failing. After reinstalling Ubuntu with a fresh GRUB, things are working fine now.

So ... now I see that 10.x is about to arrive ... am I brave or not?  Might as well try it out since I am working with a fresh machine without all of my critical data :-(

---

### Post by Barriehie on 2010-03-12
> **mne9476 said:**
> Hello ... I am back ;)

I took the suggestion of trying Debian 5,04 and used it for a day or so. I didn't notice it being any more stable than Ubuntu -- in fact, I got regular kernel faults.  It took about 5 tries to get Debian to install.

I went back to Ubuntu 9.10 -- took another few tries to get it installed, but now it's running and the only crash was Firefox after I installed Adobe Flash. I removed Firefox and Flash and reinstalled Firefox without Flash.

I am using pretty obsolete hardware which is probably the source of many of my "woes."  My specific problem this time turned out to be a corrupted MBR. I installed LILO with Debian because GRUB kept failing. After reinstalling Ubuntu with a fresh GRUB, things are working fine now.

So ... now I see that 10.x is about to arrive ... am I brave or not?  Might as well try it out since I am working with a fresh machine without all of my critical data :-(

Perhaps explore the option of putting $HOME on a seperate partition.  Then your 'data value' isn't as high!
I've gone through 3 OS' on here and with $HOME on a seperate partition it's not nearly as stressful as 'Oh no Mr. Bill, it won't boot...'  :)

---

