---
title: "Installing Ubuntu 8.10 (Overwriting/installing)"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by talking Llama on 2008-11-13
Hi. 
The title is a bit ambiguous so I'll explain. I've got hard drive A with Ubuntu 8.04 and my data on. Now I have a hard drive B which I'm going to put into my pc. Now I want to install Ubuntu 8.10 (which I have as an ISO on a CD) onto hard drive B and get rid of Ubuntu 8.04 on hard drive A. How would I go about this without royally messing things up? Keeping in mind I want to keep all my data on hard drive A but I'm not bothered about my settings from hard drive A and Ubuntu 8.04. I can just reconfigure Ubuntu 8.10.
Any help would be much appreciated so I don't mess things up and lose my data.
Thanks.

---

### Post by yt_l9 on 2008-11-13
This article should help you some:
It offers up how to switch distros without losing your data.

[http://www.techradar.com/news/software/operating-systems/the-pain-free-guide-to-switching-linux-distros-478667](http://www.techradar.com/news/software/operating-systems/the-pain-free-guide-to-switching-linux-distros-478667)

---

### Post by prshah on 2008-11-13
> **talking Llama said:**
> I've got hard drive A with Ubuntu 8.04 and my data on. Now I have a hard drive B which I'm going to put into my pc. Now I want to install Ubuntu 8.10 (which I have as an ISO on a CD) onto hard drive B and get rid of Ubuntu 8.04 on hard drive A. Keeping in mind I want to keep all my data on hard drive A but I'm not bothered about my settings from hard drive A and Ubuntu 8.04. 

Two methods suggested:

Method 1: (Recommended)[indent] a. Clone HDD A to HDD B, [using a live CD and the "dd" command]("http://ubuntuforums.org/showthread.php?t=874643").
b. Install HDD B and boot off it. Run an upgrade.
[/indent]

Method 2: [indent] a. Put HDD B into the system, and install Ubuntu 8.10 onto it. 
b. Boot into 8.10, and copy your stuff off HDD A and into suitable locations on HDD B[/indent]

In both cases, I assume you want to get rid of HDD A.

---

### Post by talking Llama on 2008-11-14
My plan is to keep hard drive A to store all my data on and hard drive B will be my OS hard drive.

---

