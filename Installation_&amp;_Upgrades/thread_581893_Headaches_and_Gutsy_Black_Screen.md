---
title: "Headaches and Gutsy Black Screen"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by fudderduds on 2007-10-19
First I had troubles upgrading, but I already downloaded the install Live CD, so I decided to go ahead and do a clean install (I don't have that many important files).  I get it all installed (after being stuck on 82% for a good hour), and now all I get after the GRUB is a pretty black screen.

I've been searching the forums, internet, and other such things for help.  I found someplace that told me that my problem was xorg.conf (at that point I was confusing black and blank screens).  I changed that, and nothing happened.

I found another place that told me to change /etc/usplash.conf to my screen resolution and run update-initramfs yada yada yada.  That didn't work. At first.

I did the above again in recovery mode instead off of the Live CD, and it solved the blank screen issue.  NOW there's this:

[  69.17200]  bcm43xx: Error: Microcode "bcm43xx_microcode5.fm" not available or load failed

What the **ck do I need to do????

I'm stuck!  I'm not like a uber ubuntu guy or anything close, I just do basic things, get online, etc.  But I really want this to work because I hate M$ (but tend to keep it on for my friend's weird samsung mp3 player), and want my Ubuntu.  

I'm seriously getting upset and might cry here.  I've been working on this for over 24 hours!  I'm going to throw my computer against a wall.
](*,)

---

### Post by pbcartwright on 2007-10-19
when you are at the black screen, if you can hit :
CTRL-ALT-F1
and get to a text-based window for login, then you have a video card issue, video DRIVER issue. probably an ATI or NVIDIA card...
your BCM error is wi-fi, which shouldn't stop you from installing or logging on..

for video errors, you need to get the right driver from those web sites.. NVIDIA has goo documentation for its drivers, I'm not familiar with ATI..
go to NVIDIA.com and go to the driver download page, read the README and have fun.

---

