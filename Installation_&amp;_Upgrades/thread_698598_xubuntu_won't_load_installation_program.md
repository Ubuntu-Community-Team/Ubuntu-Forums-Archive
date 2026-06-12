---
title: "xubuntu won't load installation program"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by munguanaweza on 2008-02-16
Hi,
I am new to this forum and hope that I have found the right one for xubuntu.  

I attempted to install xubuntu onto my harddrive, but ran into a snag.  It gets to a point where it says "saving vesa state in memory" and then just hangs up.  I am never able to get to the graphic installation program to begin the actual installation.  

I have previously installed ubuntu on the same computer but after I do program updates on it, the screen alternately freezes and unfreezes.  I had a similar problem with pcbsd on the same computer (differant harddrive) and was able to get rid of the problem by disabling powerd.  I found that fix in the ubuntu forums, and did the equivalent for ubuntu but it didn't resolve the problem.  The problem wasn't resolved in Ubuntu forums either among experienced users, so I decided to give up on ubuntu and try xubuntu instead.  Now, xubuntu is even worse.  

I will need some help to get this resolved, if possible.

Thanks.

---

### Post by dstew on 2008-02-16
How are you trying to install, Live CD or Alternate Install CD? Have you checked the CD integrity? Did you check the MD5 checksum of the .iso, and burn it at a slow speed?

If the CD is OK, and if it is a Live CD, you might have better luck using the Alternate Install CD. What are the specifications of your computer?

---

### Post by munguanaweza on 2008-02-16
Hi,
I downloaded the alternate install cd via bit torrent, and am using it to try and install.  I ran a check on the md5 check sum and used the slowest speed to burn the iso image.  When I first tried to install the cd I ran an integrity check from the menu that displays after bios has finished loading and the cd starts to load.  The integrity check of the cd is good.  When I try to actually install the OS on the harddrive is where I have the problem.  

My computer is a Dell Inspiron 5000 with a PIII600, and 512mb ram.

---

### Post by dstew on 2008-02-16
Are you using the Alternate Install CD? How much space did you make for your Ubuntu installation (root partition size)?

---

### Post by munguanaweza on 2008-02-16
Hi,
yes, I am using the alternate cd to install.  I don't have the computer with me at the moment to double check the partition size that I used, but I believe that I set it to 2.5 gb. I am on a business trip about 2000 miles from home. The documentation I read on the Xubuntu site said that it would require about 1.2 gb, for installation so I doubled it.

---

### Post by munguanaweza on 2008-02-24
Hi,
I arrived home from a business trip that I was on and was able to do a little experimentation.  I have found a solution to the problem that was preventing the installation program from loading into the computer, and am using Xubuntu to post to this forum after a successful installation.

What I did was take a look at some cheat codes, they can be found here:

[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

I set the graphics to 1024x768x16bit after selecting key F4.

Then I used key F6 to allow me to type in on command line the following when I began to install Xubuntu:

nohz=off nolapic

The system booted up fine from the Desktop CD then, and I was able to install the system to a partition on my harddrive.  I found that I had made a mistake in my earlier post, I used the Desktop CD and not the alternate CD to attempt the install previously.

I have updated the system and so far the Xubuntu system does not freeze and unfreeze as Ubuntu did when I had it installed on this computer.  Hopefully it will remain so!

---

