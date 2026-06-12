---
title: "Hardy start up issues (no resume image)"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by jdysinger on 2010-07-07
Yesterday I allowed a bunch of upgrades to be installed to Hardy. 
 
This morning I booted up and of course it doesn't recognize my NVIDIA card anymore. That's not ths issue (I have that almost memorized). 
 
I pressed ctrl + alt + F1. I received a "kinit: no resume image, doing normal boot" message and it just sat there. After some searching through the web, I edited the grub kernal line to bypass the hibernation check (quiet splash noresume). 
 
Now when I press ctrl +alt +F1, the screen reads
"Starting up...
Loading, please wait..."
 
It's sat like that for 15 minutes. 
 
Should I just go to a livecd and workaround it or is there something easier to do? Many of the previously resolved issues for the hibernation check don't really help as I'm not getting a command line...
 
Thanks!

---

### Post by dino99 on 2010-07-07
have you checked the uuid(s) (fsck -l) and the one(s) used into grub ?

---

### Post by jdysinger on 2010-07-08
I finally got it going.

I booted into the grub recovery mode and despite the warning, reinstalled the NVIDIA driver that way. 

Of course its a workaround and not a solution (incase I ever actually need to use ctl + alt _ F1). So I'll check the uuids and run from there!

---

