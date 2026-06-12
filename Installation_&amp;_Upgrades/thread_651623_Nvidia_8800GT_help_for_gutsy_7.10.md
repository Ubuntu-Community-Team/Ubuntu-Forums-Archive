---
title: "Nvidia 8800GT help for gutsy 7.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by hak33m on 2007-12-27
Hello,

I was wondering whether i could get some help with the driver installation of my Nvidia Geforce 8800GT driver..

Some background: 

I'm new to linux/ubuntu, and I'm running:

Gigabyte p35-ds3p
Nvidia Geforce 8800GT
4gb Ram

I downloaded the NVIDIA-Linux-x86-169.07-pkg1.run from the nvidia website, and attempted to install by generally following these instructions:

[http://ubuntuforums.org/showthread.php?t=648006&highlight=nvidia+8800gt](http://ubuntuforums.org/showthread.php?t=648006&highlight=nvidia+8800gt) 

although i stumbled a bit as the install returned a few messages which i wasn't expecting/ weren't mentioned..so I'm not sure if I've done everything correctly

At the moment, when i reboot, im presented with the message "ubuntu is running in low graphics mode" ...Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself"

So no matter whether i configure or continue, i am not able to direct ubuntu to the installed driver and keep my 1650x1080 resolution...I'm running a Viewsonic 20" lcd screen

Im happy to take any advice and provide any ouput..many thanks

---

### Post by Partyboi2 on 2007-12-28
Hi
Have you tried envy to install the nvidia driver? Very easy way of installing the driver.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (If you want to use it, download the .deb package)

---

### Post by wripley on 2007-12-28
how did you even manage to boot up with an 8800GT?  i can't manage to see a single thing but the black out.

---

### Post by hak33m on 2007-12-28
> **Partyboi2 said:**
> Hi
Have you tried envy to install the nvidia driver? Very easy way of installing the driver.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (If you want to use it, download the .deb package)

Ill try this when i get home..thanks for the suggestion..i saw this earlier, but then saw someone post that it didnt work for their 8800GT...


Re: How i was able to boot? lol Im not sure but i tried following some instructions about booting from the live c in safe graphics mode, then editing the splash command and adding 'noapic' , or something like that lol...

it works, even though i dont yet understand what i did...although now booting from the hard disk takes a bit longer than i woulve thought..ps im running triple boot vista/xp/ubuntu

---

### Post by hak33m on 2007-12-28
well well...
I downloaded and ran envy... everything seemed to go smoothly, however...it didnt work..

Upon restart, i get an obviously distorted picuture, where only part of  the desktop is showing, in a kind of split screen way, in either 640x480 or 800x600 resolution...i can't tell..

I also got the low graphics mode box on startup....even when i log in, and i struggle to get to the settings-->screen/resolution menu, the driver showing is still vesa, the monitor is still generic PnP...
even if i try changing these manually and logout, when i log in, its bake to the same distorted self..

SO any ideas people?

I'm losing motivation to stick with this because i seem to have problems with every step of this OS!! 

thanks

---

### Post by Drumdums on 2007-12-28
I'm having a very similar issue, except with a Radeon x800 card. I installed with the text-based alternate CD, but after "installing" drivers, it will not fire up on reboot. It just goes to a blank screen. I however can get to the CLI by starting in safemode from the GRUB. After looking around and trying a lot of possible solutions, I've given up on getting ubuntu working.

---

### Post by nosscire on 2007-12-28
I had the exakt same problem when I upgraded to a 8800GT card. Tried fixing it myself, followed guides, did everything. Never managed to get it to work though...

In the end I re-installed windows on this machine, waiting for a real working fix for the problem.

---

### Post by Pumalite on 2007-12-28
[http://ubuntuforums.org/showthread.php?t=634440](http://ubuntuforums.org/showthread.php?t=634440)

---

