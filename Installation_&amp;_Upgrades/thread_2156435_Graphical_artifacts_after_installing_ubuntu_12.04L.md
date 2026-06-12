---
title: "Graphical artifacts after installing ubuntu 12.04LTS."
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by dragonlet on 2013-06-21
I have a problem with the following artifacts after installing ubuntu 12.04 LTS.

[IMG]http://s14.postimg.org/n9sy5qbs1/scr1.png[/IMG]

I installed the distro fresh from a CD. I then installed all the updates, but this hasn't helped. I have an Asus mv2-vm mainboard with Radeon x1250 graphics. Ubuntu 10.04 has worked fine.

I would be grateful for your help.

---

### Post by Mark Phelps on 2013-06-22
Did you install, or try to install, the ATI proprietary drivers? You should be getting decent video with the default Radeon drivers.

---

### Post by cetag on 2013-06-26
My recent experience may be unrelated. I removed the 2 drives of my dual-boot Oneiric 11.10, and installed Precise 12.04LTS from ISO onto a single hdd. So for me this was a vanilla Precise 12.04LTS install onto a single drive PC (AMD Athlon, 1GB RAM). 

1. The new install of 12.04LTS, I immediately had a translucent window effect, also white squares obscuring my typed command-line in the Terminal window, etc. 
2. Firefox couldn't handle Flash video, like in YouTube. Firefox Flash upgrade didn't work. Manual Flash install/upgrade didn't improve. 
3. Email symbol in top right kept calling ThunderBird, even when I switched Default mail to Evolution. 

Thinking about this today, I remember my PC has NVidia graphic card. So I print to file dmesg of Precise installation, switch back to the 2-drive Onereic installation and print to file dmesg there. Comparing them I see that Nvidia is recognized by Oneiric, but appears nowhere in the Precise dmesg. 
 
Google Chrome, with its 'inbuilt Flash' library, didn't work well. Which must be the Nvidia drivers missing from my Precise install. 

Am not sure how to proceed here. Yes, I need a PC without Nvidia screen :) But whether Precise can be fitted with Nvidia capable drivers, I just don't know. 
So I'm back on Oneiric for the time being. I had juggled an older version Flash .so library somewhere to get Flash video going in Firefox, and guess I'll have to try the same trick with Precise once I get the Nvidia screen working. 
 
Am somewhat saddened both the Nvidia drivers and the (older?) Flash library aren't addressed in Precise.

---

