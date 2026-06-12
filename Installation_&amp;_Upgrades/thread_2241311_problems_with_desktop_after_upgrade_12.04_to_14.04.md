---
title: "problems with desktop after upgrade 12.04 to 14.04"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by scarletford on 2014-08-25
If you require additional information, tell me how to get it and I will edit this post accordingly. 

I got notified of a system upgrade to 14.04 in software updater. Clicked it to install and let it do it's thing. Rebooted and I get the log in screen. Type my password and then the desktop background comes up but nothing else. 

I have tried updating/restarting unity, ubuntu desktop, gnome, xfce, I've also tried checking additional drivers for the graphics card (there are none, it's some kind of Intel something or other), and changing xconf, none get a usable desktop. It is incredibly slow and I have lost the side launcher (even though 'hide launcher' is set to never in  ccsm). I also can't access the dash (I have tried changing the access key in ccsm but with no luck) so I have to open a terminal window and access programs through that. 

I have tried loading different desktop environments (gnome, gnome classic, gnome compiz, gnome metacity, xfce, ubuntu) and Ubuntu was showing up with launcher and dash working, but it just vanished when I was downloading the 12.04 iso to make a start up disc. All other DE's just show the background.

I have a horrible feeling that I am going to need to wipe it and start from scratch, but I am hoping someone, somewhere can help! 

I am a bit of a novice (although getting better with the vast amounts of time spent on my PC this weekend) so I may need a nudge in the right direction. 

Many thanks


EDIT: The sytem gets worse with every boot. I managed to get a back up started, only for it to not work properly and kill my machine. I've had to boot from usb, "try Ubuntu", mount my hdd and copy files over that way! 

I hope that I am more successful with a clean install!

---

### Post by kansasnoob on 2014-08-25
I've personally found that mixing entire desktop meta-packages in Ubuntu 14.04 really results in a horrendous mess :(

So I'm tempted to say that a fresh install of the proper flavor of 14.04.1 is probably the least painful way to go, but that's only my opinion and that opinion may be swayed after gathering some basic info regarding hardware:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
free -m
```

And also your current drive/partition layout:

```
sudo parted -l
```

---

