---
title: "Mouse Preferences not working with ALPS touchpad"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JoeMac42 on 2010-04-13
I have an "AlpsPS/2 ALPS GlidePoint" touchpad on an HP Mini 311 netbook.  I noticed that edge scrolling was not working following a recent Beta 2 daily build, so I went into the "Touchpad tab" of "Mouse Preferences" to make sure it was checked.  Checking "Edge scrolling" does nothing.  I checked the other options and they also do not appear to do anything.  Mouse clicks is always enabled regardless of what is checked and the option to disable touchpad while typing doesn't work.  

I also tried configuring this in xorg.conf without any success.  Edge scrolling appeared to be working fine before one of the recent daily builds, although I'm not sure Mouse Preferences ever worked since I wouldn't have gone into it if edge scrolling hadn't disappeared.

---

### Post by mockingbird on 2010-04-13
Yes I am curious as to why the option to disable the touchpad while typing is disabled with my Alps Glidepoint.  Toshiba A200 here.

---

### Post by JoeMac42 on 2010-04-14
This seems to have quit working sometime between the following two configurations:

1. Mouse Preferences working
   Synaptics TouchPad driver:  xserver-xorg-input-synaptics v. 1.2.2-1ubuntu2
   Kernel: 2.6.32-19 generic 

2. Mouse Preferences trackpad changes do not take effect
   Synaptics TouchPad driver:  xserver-xorg-input-synaptics v. 1.2.2-1ubuntu3
   Kernel: 2.6.32-20 generic

I also have a Thinkpad T60p with a SynPS/2 Synaptics TouchPad that I haven't updated/upgraded beyond configuration "1" yet.  Mouse Preferences is working fine on that machine.  I can successfully select and unselect options under the "touchpad" tab and two finger scroll is enabled as an option (currently grayed-out on the HP Mini).  I will try upgrading just the trackpad driver + it's dependencies on that machine later this evening to see if that breaks both edge scrolling and "Mouse Preferences".

---

### Post by mockingbird on 2010-04-14
> **JoeMac42 said:**
> This seems to have quit working sometime between the following two configurations<snip>

I never checked if any of the options worked, and I suspect that they do/did, but the checkbox to disable the touchpad when typing has always been greyed out for me.

---

### Post by JoeMac42 on 2010-04-15
Another piece to the puzzle - I booted my Mini 311 selecting a previous Linux kernel in Grub (2.6.31-21-generic).  Edge scrolling has returned, but now the trackpad tab is missing from "Mouse Preferences" and in "GPointing Device Settings" (something I installed during troubleshooting) no longer shows the ALPS GlidePoint trackpad in the left panel that lists pointing devices and no longer offers any configuration options. So the functions I typically use (tap to clicke, edge scroll) have returned but I have no ability to change how they function within any of the GUI tools.  I'm still a novice at this, but I would guess that I have a different trackpad driver compiled into the previous kernel and that is why edge scrolling returned.  The older driver may not be playing nice with the lucid GUI tools for configuring pointing devices but I'm not really sure.  ALPS GlidePoints are pretty common pointing devices and the HP Mini 311 is less than 1-year old, so hopefully this will get fixed soon.

---

### Post by JoeMac42 on 2010-04-15
One more thing - I tried the following last night after doing an update/upgrade at about 10 pm:
I tried creating a trackpad configuration file for udev inside “/etc/udev/rules.d”  using the instructions found at [http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html") 
and then rebooting.  None of the options that I added to the configuration file had any impact on the function of the trackpad, so I just deleted the *.rules file that I created.

---

### Post by JoeMac42 on 2010-04-15
This looks like a known bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/550625")

---

### Post by JoeMac42 on 2010-04-16
I did lsmod and no kernel module is loaded for synaptics...

---

### Post by gotsanity on 2010-04-21
anyone find a fix yet?

---

### Post by boenki on 2010-04-24
> **gotsanity said:**
> anyone find a fix yet?

There's a fixed kernel here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/70](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/70)

It fixes vertical scrolling but the preferences still don't work (here).

STeffEN

---

