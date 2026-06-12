---
title: "Another X-server problem :p"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by Buu on 2005-03-03
Hello,

I've installed Warty, but when booting it says that the x-server could not be loaded and that it is likely a configuration problem. It will disable the x-server untill the problem is fixed. First I'm able to see some x-server stuff (Xfree86.org etc.). So, I only have a console.

This may sound lame, but when installing you can choose from some resolutions for the x-server to use. Well how can I remove some resolutions, when I push enter it starts with the rest of the installation. I tryed the rest of my keyboard,
but nothing. It's stupid I know, but maybe this is part of the problem I have with the x-server.
I've tryed installing Warty again, still the same errror.

thx

---

### Post by lerrup on 2005-03-03
[QUOTE=Buu]Hello,

I've installed Warty, but when booting it says that the x-server could not be loaded and that it is likely a configuration problem. It will disable the x-server untill the problem is fixed. First I'm able to see some x-server stuff (Xfree86.org etc.). So, I only have a console.

This may sound lame, but when installing you can choose from some resolutions for the x-server to use. Well how can I remove some resolutions, when I push enter it starts with the rest of the installation. I tryed the rest of my keyboard,
but nothing. It's stupid I know, but maybe this is part of the problem I have with the x-server.
I've tryed installing Warty again, still the same errror.

thx[/QUOTE]

Are there any error messages?  How much do you know about linux - can you start a text editor and post the contents of the conf. file for X?

---

### Post by Buu on 2005-03-03
I'm rather new at Linux. 
There is not really a error message, I can look at the x-server configuration and for that posting of the content of conf. file for x-server. I'll try my best :).

---

### Post by pugrit on 2005-03-03
i got the same problem.

when it starts its on commandline then a a message pops up

"
I cannot satrt the x server (your graphical interface) it is likely that it is not set up correctly. would you like to view the x server output to diagnose the problem"

and i choose yes

some report appears about being xfree...before posting reports please check current version........

then goes back to the command line..no GUI..

whats the right configuration for the x server and where can i find it?i dont remmeber configuring one in th einsatlation process.

this is my first linux instalation expereince...i hope i can solve this though with your help guys.

thanks.

---

### Post by p!=f on 2005-03-03
What graphic card you have?
Post your /etc/X11/XF86Config-4.conf here.

---

### Post by pugrit on 2005-03-03
NVIDIA RIVA TNT@ model 64

i will have to restart first and write the conf. i will post it here though.

---

### Post by alastair on 2005-03-03
The  /etc/X11/XF86Config-4 is useful.

Bit also check the log file :

/var/log/XFree*.log (cannot reemember the name) - look for errors (especially near the end).

---

### Post by ShortyG on 2005-03-03
I'm having the exact same problem, i have a radeon 9600 SE. I know little to nothing about linux.

---

### Post by Buu on 2005-03-04
I tryed like I read on this forum somewhere in that XF86Config-4 file
to change driver 'SIS' to 'nv' because I have an NVIDIA GeForce4 Ti 4200, but then I haven no writeacces. I thought the user Ubuntu made was a superuser, apperently not. I tryed to log in as root, but no luck. And do I really have to post the full content of XF86Config-4? Quitte alot :)

---

### Post by alastair on 2005-03-04
Generally, "sudo" is used to give yourself privileges i.e.

sudo gedit <file>

---

### Post by thegeekster on 2005-03-04
You can also try using the XFree86 configuration utility from the command line. Run this command as the root user: ```
XFree86 -configure

``` and follow the steps. A new config file will be placed in the root user's home directory which can be copied over to the /etc/X11 directory..............Some installers may use a different configuration utility, which may work most of the time, but not all the time......I have found this will get you up and running, after which you can fine tune the XFree86 config file..........

If this doesn't work, it may be the necessary driver module for your video card may not loaded into the kernel.........This is especially true for some of the high-end video cards that require proprietary drivers found at the chipset maker's website (some of the nVidaia and Radeon chipsets come to mind)......

HTH :)
---thegeekster

---

### Post by Lord C on 2005-03-05
I have this problem also

When i try to startx it says "(EE) No devices Found"

Followed by "no screen found"
And X server fails to load.

I have a GeForce 6800GT.

I have tried:
xf86config
pkgreconfigure xserver-xfree86 (sp?)
xfree86 -configure
modprobe nvidia

I have also tried changing the XF86Config-4 manually.
The nv driver is being used.
I have also tried vesa and vga :/

I cannot paste any logs - I am trying to install on _this_ machine.
I have been reinstalling and trying things for over 24hours now.

aic7xxx module fails to load sometimes - maybe this is an issue?

I have SCSI drives, but they seem to function fine.
Can't really figure this one out - all other distros seem to work fine with X.

---

### Post by Buu on 2005-03-06
I have it up and running!!!
Sweeeeeet.
Thx for tha info

---

