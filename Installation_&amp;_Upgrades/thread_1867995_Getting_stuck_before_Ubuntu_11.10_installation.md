---
title: "Getting stuck before Ubuntu 11.10 installation"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by Dukenukemx on 2011-10-23
I'm trying to install Desktop Ubuntu 11.10 64-bit on my Athlon X2 system.  It has a Radeon X1950 with 2 gigs of ram.  The motherboard is biostar r690a m2t. 
I tried installing through USB memory stick, and it gets stuck.  I see a bunch of text on the screen and stops when it says freeing memory, or something.

Next I tried doing this through a DVD ISO.  See a black screen with a symbol on the bottom that shows don't touch keyboard, and eventually goes black with a blinking cursor at the upper left.  

Is there any particular reason why this is happening?

---

### Post by Dukenukemx on 2011-10-23
Tried it again, and walked away for a good 1hr too see if it got past this.  I tried using onboard video, as well as no HD.  Still stuck.  

This is the last line I see when it gets stuck.  I don't even get to the point where I can choose options.  
```
Freeing initrd memory: 14220k freed
```

**EDIT**
The old HD already had 9.04 from years ago, and it runs, but I'd rather do a clean installation to 11.10.  Clearly not the fault of my PC.

---

### Post by Dukenukemx on 2011-10-24
Don't everyone jump in at once to help me.

---

### Post by JayKay3OOO on 2011-10-24
I have no idea what the problem is.

But how come you are using 64bit on machine with 2GB ram?

32bit will be fine & if you put more RAM in (past 3GB) then you can install the pae kernel to get your 32 bit OS using up to 64? GB ram. 

To install ubuntu I always do it via flash drive. A 2GB flash drive costs about 5p these days. DVD installs never worked for me.

Use unetbootin on windows or Linux put the ISO onto a flash drive. 

Re-download the ISO too to make sure you did not get a corrupt version. Sounds silly, but I've had installs fail 'for no reason' only to find one or two files got corrupted during download.

---

### Post by Dukenukemx on 2011-10-24
> **JayKay3OOO said:**
> I have no idea what the problem is.

But how come you are using 64bit on machine with 2GB ram?

32bit will be fine & if you put more RAM in (past 3GB) then you can install the pae kernel to get your 32 bit OS using up to 64? GB ram. 

To install ubuntu I always do it via flash drive. A 2GB flash drive costs about 5p these days. DVD installs never worked for me.

Use unetbootin on windows or Linux put the ISO onto a flash drive. 

Re-download the ISO too to make sure you did not get a corrupt version. Sounds silly, but I've had installs fail 'for no reason' only to find one or two files got corrupted during download.
I just like using the 64-bit version cause I'm using this machine as a test machine.  To see how linux is doing today.  The idea is if I want to permanently switch over, I'll want to make sure it's as smooth as possible.  

I originally did do it on a 2 gig flash drive, but moved to a 1 gig I had lying around.  No difference.  Downloaded the Desktop then alternative version.  Make two different kinds of CDs from the ISO's.  Used the Universal-USB-Installer to create the USB sticks.  

I'll give that Unetbootin a try, and if I still have trouble I'll move on over to a 32-bit version.  Better to have someone reply then nothing, cause I couldn't think of what could be the cause of the problem.  I'll give these ideas a try and report back.

---

### Post by Dukenukemx on 2011-10-24
Ok, I tried installing it via unetbootin and didn't change a thing.  I tried installing a 32-bit version, and got the same results.  I have reset the bios to defaults, and nothing changed.

I'm going to see if 10.10 will install, cause I wouldn't be surprised if there's something wrong with 11.10.

---

### Post by Dukenukemx on 2011-10-25
Well, I got it working.  I had another motherboard lying around, and decided to swap it.  Both motherboards use AMD 690G based chipsets.  What I had in there originally was an old Biostar AM2 motherboard I had leftover from upgrading my PC.  Same goes for the Asus that's in there now.  

Though honestly not surprising.  The PC that had that motherboard had all bad ram.  I doubt 4 sticks of memory just went bad, so I had a feeling it had something to do with the motherboard.  Rather then replacing the motherboard with another AM2, I went and a AM3 board and bought a new AthlonII X4 processor.  I did send the memory out to be replaced, since ram has lifetime warranty, just in case I tried to resurrect a system from it.  

Oddly, the machine looked fine and even booted from a installation of Ubuntu from long ago.  Mind you this Ubuntu installation was meant for a Nforce2 system and was 9.04.  Oh well, it installs just fine now.

---

