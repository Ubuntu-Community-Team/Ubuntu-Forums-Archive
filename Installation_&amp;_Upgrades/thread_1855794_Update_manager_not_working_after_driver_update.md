---
title: "Update manager not working after driver update"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Odense on 2011-10-06
I made a clean install from a persistent USB stick on my Lenovo s10 netbook. The only apparent problem was that the proprietary broadcom driver for the wifi card was not installed so no internet (at the moment I have only access to wifi)

[praseodym]("http://ubuntuforums.org/member.php?u=1411497") kindly helped me ([http://ubuntuforums.org/showthread.php?t=1854906](http://ubuntuforums.org/showthread.php?t=1854906)) and I am posting this from the netbook - but now the update manager is not woking (there is a "stopsign" shown in the topbar (in the classic view) and when I try to open "Synaptic Package Manager" I get the following message:"An error occurred

The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

Any ideas how to fix this ? Maybe there is a way to copy the packages from the USB Stick again - or do some kind of "restoration" onlline from the Ubuntu pages ?

---

### Post by dFlyer on 2011-10-06
I may be wrong, but I believe you will need to be hard wired to the network to install the driver. You may be able to get the driver off the live cd if it worked before you installed, but you will have to set the archives to read the cd.

---

### Post by Odense on 2011-10-06
That's what I thought (and it would probably have been better but I can still do that when I HAVE access to wired net again) but praseodym helped me to get it working without a wired connection - this thread is a question on how to get the update manager and packages back to normal. I think I COULD have made the package manager read from a CD - but I used a USB stick to install and that does not seem to be covered.

---

### Post by Old_Grey_Wolf on 2011-10-07
You can get the correct file by entering these commands one at a time in the terminal:
```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Odense on 2011-10-08
Thanks - that was just what I was looking for - the netbook is now updated :D

---

### Post by mörgæs on 2011-10-08
Good, then please mark the thread 'solved'.

Hils i Odense :-)

---

### Post by Odense on 2011-11-03
Now my Samsung laptop will not update:
When I start the Update Manager it says:

**"Software Updates may be available for your computer.**
The package information was last updates 10 days ago.
Press the 'Check' button below to check for new software updates."

But when I press it I get:
"W: Failed to fetch gzip:/var/lib/apt/lists/partial/dk.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages  Hash Sum mismatch"

I naturally tried running

sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update

But this produces the same error message as pressing the 'Check' button

How can I fix this and get the Update Manager to work again ?

---

### Post by mörgæs on 2011-11-03
Have you tried changing mirror?

---

### Post by Odense on 2011-11-04
No - how do I do that ?
Please "for dummies" if possible

---

### Post by mörgæs on 2011-11-06
You can change mirror settings in Synaptic: Software sources -> 'Find best server' (or something similar).

I can not tell in all detail how it looks in 11.04, since I am on a 10.04 Ubuntu right now.

---

### Post by Odense on 2011-11-07
I could not find anything about "best server" but after I switched from the Danish Server to something like "Main Server" it seem to be working - but does that mean there is a problem withe the danish server ?

---

### Post by mörgæs on 2011-11-07
Maybe, or maybe the switching process itself did the trick. Try to switch back to Denmark - it might work now.

---

### Post by Odense on 2011-11-08
Now I found the "Best Server" so I picked that - that was not one of the danish servers though - but seems to be working :)

---

