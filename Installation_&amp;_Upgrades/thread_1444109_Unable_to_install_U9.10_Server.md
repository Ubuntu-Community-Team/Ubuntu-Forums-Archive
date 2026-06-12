---
title: "Unable to install U9.10 Server"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-03-31
Hi,
   I ran into an interesting problem. I recently purchased a Dell XPS 9000, that I intend to use as a node controller in a private UEC. I cut a new CD of Ubuntu Server 9.10 as there a a couple of show stopper bugs in 10.4 B1. I booted off the CD and the standard 4-5 selection panel appeared, I selected install Ubuntu Server and it just rebooted the machine and presented the same initial panel to choose from.  I tried re creating the cd and had the identical problem. I then installed U9.10 Desktop on a usb drive, booted from it and installed the U9.10 Desktop with no problems. 

I only saw one alternative CD image and thought, as this machine has a preconfigured raid-1 I should use it as I've had to in past desktop installs with a bios raid. That CD would not even boot, or it did boot but to a blank screen.

---

### Post by dstew on 2010-04-01
It might be the CDs have errors on them. Image CDs like these need to be burned at a very low speed, no more than 4x, because even a single bit error can cause a problem. Sound and video CDs or DVDs are much more tolerant of single-bit errors, and can be burned at high speeds. The fact that the USB system worked fine is consistent with this -- writing to a USB stick is more reliable. It also shows that the downloaded .iso is OK.

---

### Post by wcorey on 2010-04-16
Thanks for your reply. That's not necessarily it...

I was trying to install the server edition from cd, that's what I burned to cd.

When I finally 'gave up' I installed the desktop preview to a usb thumb drive and booted and installed from it. So now I have Ubuntu desktop not ubuntu server. 

I did take note of you caution regarding speed. However, Brasero does not offer 4x, only 40 and 48x I tried burning another disk at the lower speed.

---

### Post by fuzzylogic on 2010-04-16
I had a problem of "boot error" when installing 9.10, I downloaded the OS two times and put in on a disk still the same thing and this was done using window XP, finally I used an old computer with 7.04 and downloaded 9.10 and put it on a disk then reloaded OS on another computer and it worked fine. Can't explain this but 9.10 is sooo good! I'll never go back to windows.

---

### Post by wcorey on 2010-04-22
> **fuzzylogic said:**
> I had a problem of "boot error" when installing 9.10, I downloaded the OS two times and put in on a disk still the same thing and this was done using window XP, finally I used an old computer with 7.04 and downloaded 9.10 and put it on a disk then reloaded OS on another computer and it worked fine. Can't explain this but 9.10 is sooo good! I'll never go back to windows.

Oh, I know...."I hear that!"

I am waiting with bated breath until next Thursday. I am very excited about 10.4, especially the LTS nature of it. Mostly though I want to reconfigure my two system environment to be a cloud. Effectively then Ubuntu on the metal will merely be a hypervisor and node controller. I can then have production and test images running simultaneously and independently so anything ill happening in one will never affect the others.

I do wish Evolution actually reliably did Exchange and Ubuntu/Debian repositories/apt weren't plagued with hash sum mismatch problems which has been plaguing me for over a month now.

---

### Post by wcorey on 2010-05-04
I thought I'd update this thread with some information I just 'discovered' last night.  After creating an install cd, note there is a file on it called md5sum.txt

cd to /Media/cdrom

issue:

md5sum -cq md5sum.txt

It will silently compare the md5 hashes against each file and report on the ones that do not compare.

Ironically the only one that did compare as perfect was the 10.4 server disk I burned the other day.

Had I know this, I would have saved myself hours of frustration. Hopefully this will save the reader hours of that same frustration.

tag: md5 md5sum verify

---

