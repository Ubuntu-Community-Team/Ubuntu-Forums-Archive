---
title: "Cedarview GMA 3600 with Ubuntu 12.04"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by pineda-christopher98 on 2015-03-15
Hey Guys, so i have a Redfox Defianz, it's a Local Philippine MacBook Pro like Laptop but it has Intel GMA 3600 integrated coming from the Atom D2700, i know that You can not install GMA 3600 on Ubuntu, but i got the version 12.04 LTS and i changed my kernel from 3.13xxx to 3.2xxx (can't remember, they also said changing my kernel, driver should work) i rebooted then i go to terminal and follow these instructions,

[https://ef.gy/ubuntu-cedarview-drivers](https://ef.gy/ubuntu-cedarview-drivers) . then i rebooted again, now instead redirecting to the Log-in Screen and there is a error windows, please refer to the picture

[ATTACH=CONFIG]260627[/ATTACH]

i would be so happy if you can help me out, thanks! :D

---

### Post by coffeecat on 2015-03-15
@pineda-christopher89, your thread title "The Syste" would not attract those who could help you with this problematic graphics chipset, so I've changed it to something more suitable. I've also made your link clickable for the convenience of who might be able to help.

I suggest you clarify the exact steps you took to replace the kernel because it appears to be different from what is recommended in your link.

---

### Post by pineda-christopher98 on 2015-03-15
sorry didn't check my thread before posting it to public, thanks for correcting it, i removed my kernel 3.13.xx and installed 3.2.xx through Synaptic Package Manager, then before typing reboot on terminal i typed sudo update-grub  on terminal then enter reboot, after booting, i booted on a  1024x768 resolution, i checked if i succesfully removed kernel 3.13 and installed 3.2 by typing "uname -r" on terminal , and the result was 3.2.xxxx-generic which ment it was successful, so i started to follow the instructions on the website that i inlclude in this thread, i typed "apt-get update then" [COLOR=#000000][FONT=monospace] "apt-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**get**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**install**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers" then all was success, then i type "reboot" terminal to restart, thats's what i did so far, after that, i boot up instead of login screen, as what i said, some sort of a black background screen with a windows saying  "The system is running on low graphic mode", 


Ofcourse, i did some research for this problem, there's a solution i found that some many people fixed their problem, i tried that solution, pressing shift key while booting and boot up on recovery mode with the 3.2.xx kernel then selecting the FailSafe mode, after that there were a bunch of white text appearing  and after a couple of seconds, it all went to blank screen with some sort of like a blinking underscore on the top left on my screen, i left it on till 5 minutes until i gave up waiting because nothing is happening, i can't even restart the Laptop by pressing ctrl + alt + del but didn't work, so i ended up pressing the power button for 5 seconds to force it to shut down and ended up using my another Laptop to create this thread, hope that gives you some information

[/FONT][/COLOR]

---

### Post by fantab on 2015-03-15
I had this on my eeepc. It is a pain to manage this 3600 in linux. My best option was to use the generic opensource drivers. You will sacrifice HD playback/videos, apart from that every thing else worked fine. I had installed Bodhilinux and Fedora both worked out of the box minus HD Video playback.

Those drivers you are refering to only work with 32bit ubuntu. Are you using the 32bit? Even for Windows the driver is for 32bit only. Even with proper driver the HD playback in Windows too is not a great experience.
I never really got those driver to work... 

Bodhilinux is based on Ubuntu LTS... I found Fedora to somehow perform better than *buntu with GMA3600 on board.
So, if HD playback is not an issue then use the generic graphic drivers.

---

### Post by pineda-christopher98 on 2015-03-16
Damn, i always watch TopGear on 720p , is there any other way to install GMA 3600 driver? or atleast make it work? they said that changing the kernel to 3.2 will work, and Yes i have 12.04 LTS 32-bit, without the GMA 3600 driver, flash videos are still good even playing on 1080p in YouTube is not a problem, however playing a video file on the computer using the preinstalled Video player on ubuntu, the framerates are laggy, even the video or the movie i was playing is only on 640x480, i tried to try these stuff before,

---

