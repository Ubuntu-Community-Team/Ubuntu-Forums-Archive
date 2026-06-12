---
title: "Installation FAILED - CD is 100% fine"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by bcn17 on 2008-06-14
I came home from school for the summer ready reformat my mom's computer to ubuntu and rid her of windows- I go ahead and pop in ubuntu-  8.04 alternate and when it gets to the installation step to "load installer components from cd" it says that it failed. 

I have done several memory tests-
verified the cd- (it fails) but I popped in the same cd on my computer and it passes 100%- 
To be sure I downloaded the .iso again and it still passes on my computer 100% but her computer gives me a FAILED with a very bright red screen. 

the computer is a compaq w/ 

athalon 64 3400 
1 GB ram
ati videocard- not sure on exact model- I'll check l8er but it shouln't be the problem considering its an alternate cd and it's at the very beginning of the install. (although I have had ati videocard problems before in a big way- but after the install on the first boot up )

Right now I'm downloading windows updates because I reformatted the windows partition anyways- please save me so I can get rid of windows!! :)

---

### Post by overdrank on 2008-06-14
> **bcn17 said:**
> I came home from school for the summer ready reformat my mom's computer to ubuntu and rid her of windows- I go ahead and pop in ubuntu-  8.04 alternate and when it gets to the installation step to "load installer components from cd" it says that it failed. 

I have done several memory tests-
verified the cd- (it fails) but I popped in the same cd on my computer and it passes 100%- 
To be sure I downloaded the .iso again and it still passes on my computer 100% but her computer gives me a FAILED with a very bright red screen. 

the computer is a compaq w/ 

athalon 64 3400 
1 GB ram
ati videocard- not sure on exact model- I'll check l8er but it shouln't be the problem considering its an alternate cd and it's at the very beginning of the install. (although I have had ati videocard problems before in a big way- but after the install on the first boot up )

Right now I'm downloading windows updates because I reformatted the windows partition anyways- please save me so I can get rid of windows!! :)

HI and it could be the speed of the burn. I am assuming you are burning the cd's on your system and that maybe why they have passed on yours. I have had this happen with a fast burn.

---

### Post by Rustafur on 2008-06-14
The reading heads on either your, or your mom's, computer may not line up exactly either. Sometimes, if a PC gets dropped, or smacked pretty hard it can throw your CD/DVD disc drive's head out of alignment. This would cause you to either burn CD's that are just little bit off, or would cause your mom's PC to not be able to read discs that are burned from other computers. I had this problem with an older system of mine that I used to tote around to LAN parties. It was a rather large and heavy case, so it got dropped and bumped and banged around more than it's fair share, which lead to the drive head getting bumped out of calibration.

---

### Post by paddy1 on 2008-06-14
I have installed Ubunto on many Athlon and Celeron computers. My trick, (especially if the computer has run windows) is to use the Maxtor disk diagnostic utility, and run a full, low level format of the drive. I then use a win98 startup disk to partition the drive, and then start the CD install. Works every time for me.

Recycling and refurbishing older computers and donating to those in need

---

### Post by bcn17 on 2008-06-15
So I did several very low level formats- not with maxtor's utility though- I used an active kill disk from herons boot cd. This did not work- Next I switched out the cdrom, although it was one that in the past gave me troubles reading and writing on a windows machine, So it wasn't the best test. I did get past the part where it was loading components but it then froze again with the same type of problem! I have decided to try and install with a usb drive- It's boots up to it fine but I am having trouble mounting my usb drive- (In my case /dev/sdb1 ) to /cdrom. 

I did it the automatic ways to no avail- manual worked except for that it won't mount to /cdrom so it boots up but still won't work. I used the alternate cd it seem from the literature that I won't have to do the extra mount step with a live cd so I'm gonna try a live cd on the disk drive. This is turning into a totally different topic though! Thanks for the ideas though guys! 

*In case you have the same original problem keep in mind using a usb drive or network install. See here for usb install- manual is the only method I got to boot into the install screen. 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

EDIT: here is the link for my usb drive problem if you want to take a look:

           [http://ubuntuforums.org/showthread.php?t=831332](http://ubuntuforums.org/showthread.php?t=831332)

---

