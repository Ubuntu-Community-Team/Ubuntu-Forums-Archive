---
title: "installing nvida driver fail for a server?"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by bob146 on 2015-08-31
I was trying to install the nvidia driver for my graphic card (gforce 460M) on Ubuntu 14.04 Lts and in the middle of the installation I get 2 separate error screens.  This is the way I tried to install the file
```
cd Downloads
chmod +x NVIDIA-Linux-x86_64-352.41.run
sudo ./NVIDIA-Linux-x86_64-352.41.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 352.41......................"
```
So I went to the nvidia log file and pulled this out - these are the same 2 error screens I received about running a server. 
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug 31 00:39:01 2015
installer version: 352.41

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> Detected 8 CPUs online; setting concurrency level to 8.
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '3138' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 

ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details. 
I am stumped here, the file  .X0-lock' does not appear in the tmp folder.   what is Process ID 3138? I tried to find it in the process but when i got it loaded that didn't show up (sorry) The internet has dozens from a Norton error to perl coding.  

What did I do wrong?  and is there a way to fix this?   In short I need some professional help ( YES that kind also :p )  any help given would be much appreciative

---

### Post by dino99 on 2015-08-31
avoid using the .run file from nvidia; instead activate the xorg-edgers ppa, update, install the nvidia-352 package, then deactivate the ppa and update again

[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

---

### Post by bob146 on 2015-08-31
Thank you  I ran off to try that and it  still errors with server X.   It always goes to this "running a server X" and i cant figure out why it thinks I am.  I am not even close to being a novice with linux just learning (and screwing things up along the way) but his nvida file thing is really getting on my last nerve here.  this is what i just got from the install of the 352 file
[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug 31 11:25:19 2015
installer version: 352.41

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> Detected 8 CPUs online; setting concurrency level to 8.
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1233' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.[/HTML]
I don&#8217;t want to sound like an idiot but apparently this is smarter than I am,  Do I need to do a fresh install again to make sure I am running a desktop ONLY?


when i try to install th x-org 352 files this happens  now this is on a fresh install nothing else has been installed yet.   same results matter what I do. Tell me this is it the fact i'm to dumb to learn this or is my laptop just screwing with me 
Toshiba Qosmio x505
intel I=7 2 ghz
8 gig memory
twin 500 gig Hd  Umbuntu on d drive  (sdb i think its called)
Nvidia gforce gtx 450m

sorry for the large pic   I haven't learned how to crop them yet  
[IMG]http://s25.postimg.org/8n6u6ax27/Screenshot_from_2015_08_31_17_07_27.png[/IMG]

---

### Post by efflandt on 2015-09-01
As mentioned it is best to use Ubuntu packages instead of a .run file from nvidia.com because the packages are coordinated with X and other things in the system and will update automatically if you do updates when the Software Updater comes up. The .run file it is telling you that it cannot run while X is running and you are obviously running X in your screen shot. I don't remember the exact command to stop/start X from a text terminal (Ctrl+Alt+F1 thru F6 takes you to a text terminal, and Alt+F7 takes you back to X or gui login). So if you insist on using the .run file, you could boot a (recovery mode) selection from grub, enable networking (which remounts your drive from read-only to read-write), then select Root Console and run your .run file from there.

I don't know if attempting to install that partially installed anything or would interfere with installing an nvidia package. Normally from the desktop you would run **Additional Drivers** from the icon at top left and see if it comes up with suggestions. If you have hybrid graphics (combo Intel/Nvidia) and it does not come up with nvidia drivers, install **synaptic** from Software Center (the bag icon), run synaptic and hit the curly icon to update packages, then enter **nvidia** in Quick search, and install **nvidia-331-updates**. I don't think you should need anything newer than that (which currently installs a 340 driver) because that is what I am using on my laptop that has hybrid Intel HD 4600 / Nvidia GTX 765M graphics.

---

### Post by mansonfan78 on 2015-09-01
You can't install those from the desktop.  Do ctrl-alt-f1 and at the prompt log in to your account.  Then type  sudo service gdm stop (or lightdm, kdm, mdm, whatever you're using).  Then you can cd to the directory and enter the commands you tried before.  After installing (if successful) it's best to reboot.

---

