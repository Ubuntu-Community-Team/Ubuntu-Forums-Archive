---
title: "Problems Installing Adobe Flash Player from Synaptic in Ubuntu Studio 10.4 x64"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by tnasty on 2010-08-14
When I try to install Adobe Flash Player from Synaptic in Ubuntu Studio 10.4 x64, A window pops up which tells me and asks me to do the the following:


CD/DVD 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)' is required

Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from the medium.


When I follow these instructions and click continue, the pop up window does not go away. It tells me to do the same thing over and over. If i hit cancel, it tells me the following:


W: Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/pool/main/a/alsa-lib/lib32asound2_1.0.22-0ubuntu7_amd64.deb
  

I did not run into these issues at all in regular ubuntu 10.4 x64. Please help. 

Thank you,

Mr. TNasty

---

### Post by tnasty on 2010-08-14
PROBLEM SOLVED!

I just typed name of the file that my system was trying to get off the boot disk ([lib32asound2_1.0.22-0ubuntu7_amd64.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/lib32asound2_1.0.22-0ubuntu7_amd64.deb")) into Google, found a place to download it at:

[https://launchpad.net/ubuntu/+archive/primary/+sourcepub/1073049/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/1073049/+listing-archive-extra)

(it was the 2nd result of my Google search), downloaded it, installed it, and then installed the rest of the flash player from the synaptic package manager and everything worked

Cheers,
Mr. TNasty

---

