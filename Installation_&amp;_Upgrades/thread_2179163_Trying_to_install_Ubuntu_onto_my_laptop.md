---
title: "Trying to install Ubuntu onto my laptop"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by Brotell1950 on 2013-10-06
I am currently using windows 8 and its becoming painful so I have decided to come back to Ubuntu but when I put the disk in at boot up all I can see is the start area which asks me to install with out changes etc but when the disk starts to read my screen just stays blank never had this happen before.

The laptop is a 64 bit HP 650.

Any ideas will be appreciated.

Regards

Terry

---

### Post by fantab on 2013-10-07
Can you "Try Ubuntu without installing"?
What Graphics card do you have in there?
If Win8 came pre-installed, does it boot in UEFI or BIOS?
If it boots in BIOS mode then  HP usually has all the four Primary partitions used up... this can causes the Ubuntu installer not to see or recognize the Hard Disk....

Try the [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") option. If its a graphics issue then it can take care of it.

---

### Post by Brotell1950 on 2013-10-12
Graphics card is Intel HD Graphics 3000
Boot is UEFI

How do I get to NOMODESET at setup all I get is basic start up ie do you want to try Ubuntu with out installing and install Ubuntu


terry

---

### Post by ubfan1 on 2013-10-13
At the black grub screen with the try/install, type "e" (without the quotes) and add the nomodeset to the line starting with linux just after the
"quiet splash" and before the --
Then F10 or ctrl X to boot, instructions should be at bottom of screen.

---

### Post by Brotell1950 on 2013-10-13
no joy still black screen

Terry

---

### Post by Sinixstar on 2013-10-13
Check this out : 
[https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer](https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer)

I had the exact same problem trying to setup on a macbook air - this took care of it.
What I found on my MBA was once it was set up and installed everything was fine, but on the initial load the video just was not happy. Never dug into the details of why, and frankly didn't much care since it worked once I got it installed. It was only running off the live key during install there was an issue.

---

### Post by Brotell1950 on 2013-10-13
no place in bios to disable frame buffer

Terry

---

### Post by Sinixstar on 2013-10-13
> **Brotell1950 said:**
> no place in bios to disable frame buffer

Terry

You don't need to do it in the bios - you can set the flags in grub so that it disables. the "nofb" flag specifically. 
Actually - if I recall - on my MBA, i actually set "framebuffer=0" somewhere, and that worked too - but the docs seem to not mention that.

---

### Post by Brotell1950 on 2013-10-13
mY problem I cannot get a linux distro to work so using flags in grub is a mote point.

Terry

---

### Post by Sinixstar on 2013-10-13
> **Brotell1950 said:**
> mY problem I cannot get a linux distro to work so using flags in grub is a mote point.

Terry


Yea, sorry - it's been awhile since I've had to mess with it. I know there is a place where you can get that setting in there on the liveUSB setup. I do not recall off the top of my head, but I know it's there.

---

### Post by Brotell1950 on 2013-10-13
SOLVED


Solved my problem enable legacy boot
The only distro I could get working was Ubuntu 13.04 64 bit but its a start

Terry

---

