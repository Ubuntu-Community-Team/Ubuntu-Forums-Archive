---
title: "Stupid Question about Installation"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by bhocay on 2008-03-15
[SIZE="6"][SIZE="3"]okay here it goes..

i was installing ATi VGA driver.. and it was perfect
i typed bla..bla..bla..

wogh! and it ROcks
thanks to [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
but

i am curious... what the hell is happening what've i done..
yes i've succed to install the driver

Then i have question in mind
Q:but what did happen? 
A:I dont know:confused:

Q:What have i done to the kernel, it seem compiling that and compiling this?
A:I dont know :confused:
 
Q:What Have i done to the Xorg?
A:I dont know :confused:

Q:My desktop always start with 1600 res, auch it hurt with 17" tube, iF i change to 1024 res then it work temporary on the next restart.. :confused: what happened
A:i Dont Know, I just follow the instruction..

Q:Can u fix it...
A:NO..

so the point is.. **Some body tell me what in the name of Tux.. what i've i done**?(by following the Guide)

Cozz i want to know what is happening to my kernel and system config.. TQ :)
 [/SIZE][/SIZE]

---

### Post by Lord Landis on 2008-03-16
> **bhocay said:**
> [SIZE="6"][SIZE="3"]i am curious... what the hell is happening what've i done..
yes i've succed to install the driver

Then i have question in mind
Q:but what did happen? 
A:I dont know:confused:

Q:What have i done to the kernel, it seem compiling that and compiling this?
A:I dont know :confused:
 
Q:What Have i done to the Xorg?
A:I dont know :confused:

Q:My desktop always start with 1600 res, auch it hurt with 17" tube, iF i change to 1024 res then it work temporary on the next restart.. :confused: what happened
A:i Dont Know, I just follow the instruction..

Q:Can u fix it...
A:NO..
 [/SIZE][/SIZE]

What you've done is created a module for your graphics card and rolled it into the kernel.  Any time you add a module that isn't there by default (the ATI driver in this case), you have to re-compile so that the kernel can actually make use of it.

You haven't done anything to Xorg itself.  All you've done is told it to use the new driver that you've compiled and activated in the kernel.

You're saying that you want your system to start X at a lower resolution?  You can make this a permanent change by modifying your xorg configuration file.  The safest way to do this is to run the xorg configuration.  In a terminal, do the following:
[code]sudo dpkg-reconfigure xserver-xorg[code]

It will walk you through the configuration process.  When it gets to your monitor, choose the advanced  option (or maybe the second one...) so that you can pick your own resolution and refresh rate settings.  It will present you with a list of resolutions, at which time you simply check the ones you want.  X automatically tries to start at the highest resolution specified in '/etc/X11/xorg.conf'.  If you don't check 1600, it won't even try to use it.  Note that you could also edit the config file by hand, but doing so can seriously bork your system if you screw something up.  So if you're going to try to edit it manually, make sure that you back it up first!

---

### Post by bhocay on 2008-03-16
**WOW** THANKS MAN .. IT WORKS..  You ROCKS :guitar:
SOry becozz of my foolish.. im Just a NEWbie :)

---

### Post by Lord Landis on 2008-03-18
Glad to be of help.  We all ask questions like that when we first start with Linux - it's how we learn.

---

