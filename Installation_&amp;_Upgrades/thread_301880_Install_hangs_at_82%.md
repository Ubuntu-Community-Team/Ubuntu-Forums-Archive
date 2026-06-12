---
title: "Install hangs at 82%"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by jimmykuruvilla on 2006-11-17
Hi all,

    I've been trying to install ubuntu 6.10 from the livecd and I everything seems to go well until 82%. I'm sorry I don't have the exact error message, but it was something like "Configuring APT, CPT or NPT..."

No matter how long I wait the progress meter doesn't move. The live session works fine even though the install has gotten stuck. 
I tried the x386 and x64 versions (running amd 64) with no luck.

I thought it might be trying to sync something online, because I get a similar problem with internet access. Strangely I can go to any google page...literally anything that has a google label on it (pages, video, image search, groups etc.) but I cannot go anywhere else. When I try, I don't get a timed out message, it just says "waiting for www.website.com."

In the past when I have tried to install Ubuntu 5.10, I never had use of my ethernet card. I think support for it was recently added. 

My mobo: ASUS K8S-MX
more importantly the ethernet device is on board: SiS 190 100/10. 
AMD 64: 3200

Any help would be very appreciated. 

~jimmy

also the CD check prior to loading the x386 version gave me "1 checksum error." Possible issue?

---

### Post by pay on 2006-11-17
The cd may be corrupted. You might need to download a new one.

---

### Post by Bartender on 2006-11-17
It's pointless to proceed with installing if you got checksum errors.  You need to go back a few steps.  Your downloaded .iso file must be compared to the checksum value listed on the download website.  The .iso is one huge file, so there's just one md5.  Any number of md5 utilities (Linux or Windows) will generate an md5 from your download.  Since there's only one you can visually check the 2 values in a minute or 2.
The bootable CD is another matter entirely.  There are hundreds of files on the CD.  If you have a known good CD you can use the same Linux-based or Windows-based md5 (I like md5Summer in Windows just cause it's relatively easy) utilities to create a long list of md5's from the known-good CD, then use the utility's comparison feature to compare a second CD.  The "Check CD for Defects" feature built into the Ubuntu CD apparently does that for you.  I've read that the "Check" is not 100% foolproof but it probly should be considered as a good indication nonetheless.

So, long story short, you have to check the download to make sure it's viable.  If it is, then you need to burn it slowly using a good quality CD and run the "Check CD" function again.

---

### Post by jimmykuruvilla on 2006-11-18
Thanks for the replies guys. I checked my iso files with md5 summer, and they didn't match the listed hashes. So I downloaded them again, this time thorough utorrent, and a direct download and those hashes don't match either. Is it usual for downloads to be different like this? Thanks again.

~jimmy

---

### Post by pay on 2006-11-24
It is annoying, but not unusual.

---

