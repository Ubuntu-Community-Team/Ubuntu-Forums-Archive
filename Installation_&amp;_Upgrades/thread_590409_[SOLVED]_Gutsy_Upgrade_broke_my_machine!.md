---
title: "[SOLVED] Gutsy Upgrade broke my machine!"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by thorner on 2007-10-24
Hi Everyone, 
I have about had it with the Ubuntu upgrades. Always something broken, since I started using Linux (Dapper) I have yet to do a smooth upgrade. (PCLinuxOS is looking good....;))

Please help.

Every boot seems to be slightly different. But never correct. Sometimes I get nothing but a command prompt, sometimes an error message about the Xserver. After reading through some posts and doing things like apt-get remove gdm and re-install, and then I manually loaded nvidia 100.14.11 driver, it 'half works'. I can at least get a GUI now, however it keeps defaulting to 'plu&play' monitor with 600x800 res.  

I'm not a Linux wiz, and I have tried what I know, plus a few things found on this forum. More help would be stellar. Especially before my wife finds out I've broken the computer again :)!

Cheers,
Tim

---

### Post by thorner on 2007-10-24
I should mention that my sound doesn't work as well, and on boot, I get a kernel panic error, and need to do about 4-5 resets before I can boot to either the GUI or command prompt. Might be the root of the problem? Please help.

AMD64 X2 4000+
Nvidia 6600 128MB

---

### Post by thorner on 2007-10-24
Something else that may help in diagnosing the problem, after manually installing nvidia driver 100.14.19 I was able to add a check in the box beside NVIDIA Accelerated graphics...  in System>Administration>Restricted Drivers. then it just disappeared and when i 're-check' it, I get this error:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19
+2.6.22.4-14.9_amd64.deb: subprocess pre-installation script returned
error exit status 2

Thanks!

---

### Post by thorner on 2007-10-24
Anyone? Please :)

---

### Post by JoBangles on 2007-10-24
I have lost my VDU display. I upgraded using the upgrade option, noted 3rd party software was disconnected, chose to save some sort of configuration file, noted a comment to the effect " some software my be logging/blocking keyboard" clicked O.K. all went well, noted some graphics changes and rebooted as requested. System loaded to first "Ubuntu" flash screen then screen went black, VDU power button started flashing, hard drive flashed on and off then stayed on for 10 minutes until I shut down. I booted into recovery mode to see if I could select the old xorg.conf file but it was gone. Now I do not know what to do. (This comes to you via dual boot WinXP) Any help greatly appreciated.

---

### Post by JoBangles on 2007-10-24
This fixed my problem hope it helps. http:ubuntuforums.org/showthread.php?t=187177

---

### Post by mpstump on 2007-10-24
Tim, I'm having the same problem, I'm thinking of getting a new wife ;)

I've tried everything that I can find on nvidia drivers, so far no magic bullet. Some of the tips include enabling "restricted drivers", which does everything but work properly for me. I should add that I'm using Kubuntu, so I go to start/settings/advanced/restricted drivers (log in as adminstrator at this point)./ enable. 

The other thing that I found out was that the kernel that was loading didn't support SMP, or my hyper-threading/ multiple  processors. I re-arranged the /boot/grub/menu.lst file to load the generic kernel instead of the 386 one. 

Have you tried Envy yet? ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) Some people swear by it,  but I've also been told via chat that it can cause further problems (which may be why I haven't got it working yet).

Hope all goes well. If you find a solution that works, update please!!!

---

### Post by gtdaqua on 2007-10-25
I had similar problems - actuall I still do. I didnt install the Nvidia restricted driver because it craps my system. I downloaded the latest (100.14.23 and not 100.14.11) from nvidia and did a fresh install. You have to do some tweaks though after installing. You need to have the Ubuntu kernel source (although Ubuntu says 'headers' are ok) and then u need to disable the restricted modules from loading automatically so that the latest NVIDIA drivers could work!! 

Its becoming a pain now because we never had these sort of problems in Windows. Linux problems are unique and sometimes (actually more) its a complete waste of time! 

WE NEED SIMPLE OPERATING SYSTEM. EASY INSTALLATIONS AS IN WINDOWS AND THE SPEED OF LINUX.

---

### Post by thorner on 2007-10-25
Yeah, I agree, a new wife might be the way to go ;) or buy her a laptop to keep her happy...

I have tried envy in the past, and it worked great until I started playing around with MythTV and Dual monitor support. I had to remove envy and reinstall the drivers manually No easy task for a newbie.. So I'm a little hesitant to try it again. but I will, and see what happens....

---

### Post by thorner on 2007-10-28
Got it to work! I tried Alberto Milone's Envy again. Worked great, Thanks Alberto!

---

### Post by mpstump on 2007-10-29
I got mine working this weekend too. I gave up and installed Gutsy on a fresh hard drive, and then copied /home over. I know, I cheated, but I couldn't spend any more time messing it.  The drivers from the Nvidia website worked, so I didn't use Envy.  My apologies to Alberto, and the Ubuntu team if they heard my cursing last week, since I think the problem was 'operator error'.

During this fiasco, I tried out PcLinuxOS. With the KDE interface, it was similar to Kubuntu, but in the end, I still wanted Kubuntu back. 

Not sure what to do with the wife though...

---

