---
title: "Ubuntu Installation on Alienware m5550 Laptop"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by cray001 on 2007-10-25
Hi, I have no experience with Ubuntu whatsoever, or any with Linux for that matter, so I'd like to apologize for anything simple that may have gone/go over my head.   

I'm running an Alienware m5550 laptop with Vista and I decided recently that I'd like to dual-boot Ubuntu.  Unfortunately, I'm having trouble installing it.  

I followed the instructions on creating the boot disk, made it, resized my Vista partition so that I have ~20 gigs of unallocated space, and booted from the CD.  

This brings me to an Ubuntu menu, the first two options of which ("Install or Run Ubuntu" or something along those lines, and "Run Ubuntu in Safe Graphics Mode") I attempted several times.  Each time things start of well enough--a bunch of scrolling white text on a black background--but then there's a pause and my screen flashes a very distorted image.  Soon after, it fades away, goes back to the black screen with white text, and repeats the process.  After doing this several times, the screen becomes blue with a white box in the middle that has an error message which reads: 

"The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0."

Then there's an apparently highlighted red box around the choice of "<Ok>".

Hitting enter brings me back to the black and white text, and after some time, the same distorted picture flashes, and the same blue screen comes up.  

Could/would anybody help me with this?  Thanks!

My hardware, if it helps, is:
Intel Core 2 Duo Processor T7400 2.16GHz 
128MB ATI Mobility Radeon X1400
2GB Dual Channel DDR2 SO-DIMM at 667MHz
160GB SATA 1.5Gb/s 7,200RPM
Alienware Intel 945PM + ICH7 Chipset (of course)

EDIT: Whoops, added in my hard drive.

---

### Post by Pumalite on 2007-10-25
Use Alternate CD to install. Do md5sum on iso, burn at 4x, burn as 'Image' not as 'data'.

---

### Post by cray001 on 2007-10-25
Still not working, I'm afraid.  

I did as instructed, and it seemed to have installed fine.  I took the CD out as instructed and hit continue, and the computer restarted.  I had the GRUB loader or whatever start up, and I chose to run Ubuntu from the menu.  The logo came up, the bar filled, and then the screen went to the black and white text.  

But then, the same sort of distorted picture flashed as before, and, as before, it repeated this several times before showing a similar blue screen with the same message as in my first post.

Any suggestions?

And again, thanks ahead of time!

---

### Post by JPorter on 2007-10-28
> **Pumalite said:**
> Use Alternate CD to install. Do md5sum on iso, burn at 4x, burn as 'Image' not as 'data'.

Would people PLEASE stop suggesting this to every person who posts a problem?

I'm having the exact same issue after installing on my laptop with the Alternate CD, and this is the same CD that I used yesterday to do a successful install on another computer.  MD5 checks perfecly and it was a 4X burn.

---

### Post by Pumalite on 2007-10-28
The Alternate CD is exactly to solve graphics problems, and to have an ATI today is a graphics problem in Linux since ATI does not support Linux. Vote with your pocket and buy an Nvidia.

---

### Post by JPorter on 2007-10-28
> **Pumalite said:**
> The Alternate CD is exactly to solve graphics problems, and to have an ATI today is a graphics problem in Linux since ATI does not support Linux. Vote with your pocket and buy an Nvidia.

Ok, I'm going to do what you failed to do, and provide a solution:



The issue is the same old problem... the fglrx driver is sometimes required to start xorg without corruption on newer ATI cards.


You will need wired internet access.  Boot to recovery console and do this:
```
sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv
```

If your first step failed because you didn't have internet access, you should run:```
sudo ifconfig eth0 down

sudo dhclient eth0
```

Of course, substitute eth0 for whatever your ethernet connection is (eth1, etc).  Follow the above driver install steps.



And then reboot normally.  Voila, you should be up and running.

---

### Post by Pumalite on 2007-10-28
I would add this if things don't work:
sudo aticonfig --overlay-type=Xv

---

