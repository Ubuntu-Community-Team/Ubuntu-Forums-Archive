---
title: "Missing APT Method drivers"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by kjbuente on 2008-05-13
I am running Hardy on a AMD64 cpu, the problem is that this PC has no internet connection and I want to keep it upgraded and need to install some apps. Did some reading and I came to my solutions. I've been using debmirror and mirrored the repos on my laptop. (laptop running 32bit ubuntu, plus a nice 10Mbit fiber pipe at work). I was able to download the main,universe,multiverise, and restricted in 2 hours.

So, I have everything downloaded to my laptop. Time to figure out how to point my desktop to my PC, well I read on one of the on-line ubuntu documents that I can use samba to pint my sources.list. So I set my sources to my laptop and the directory that I have shared. When I tried it to see if it worked it errored out saying that it could not find the smb method driver. If I can find the link again I'll post it.

So the questions really are...

How do I install the method driver for APT? 
Or is there another method out there that I can use. I do NOT want to start an HTTP or ftp service on my laptop. Perhaps mount my share to a folder and point it using file:///path/to/repo. Whould that work?

Since I have the repo on my laptop, I can find packages if there needed and transfer them on to the PC and install them.

Any insight would be nice. I have also looked into APTonCD, but will not work best for my situation. Simply pointing it to a local point on my network is faster since I do not have burn any disks.

Thanks!

EDIT: [Here's the link]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-8a18d4250a1c368b58239ba0d6fcc4e5639fa42f")

---

### Post by kjbuente on 2008-05-13
Well, I decided to install a ftp deamon. (Pureftpd). Decided to go this route for better management. Still wondering how to get the method drivers for apt...

---

