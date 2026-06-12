---
title: "can't get high resolution with Ubuntu 7.04"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by markux on 2007-05-27
I have tried to install Ubuntu on my machine and can't get high resolution working.  Can someone please show me how to do that.  When I run the live CD it give me the high resolution alright so I think it does recognize my video card and loads the appropriate driver and set Xorg.config right.  

Thanks

---

### Post by old_geekster on 2007-05-28
> **markux said:**
> I have tried to install Ubuntu on my machine and can't get high resolution working.  Can someone please show me how to do that.  When I run the live CD it give me the high resolution alright so I think it does recognize my video card and loads the appropriate driver and set Xorg.config right.  

Thanks
This appears to be a bug in Feisty.  I have to set the resolution everytime that I boot.  For whatever reason, it simply will not hold.

I am certain that this has been reported, but there has not been a fix to date.

If there is a fix, I hope someone will tell both of us about it.

---

### Post by markux on 2007-05-29
Since this happens during installation it makes the process very difficult; the major navigation keys at the bottom of installation screen is hidden and installation must be abundant.  I am curious to know that if this issue is a bug and a general problem how do other user go around it and install the system.  I have tried to remedy this by hiding and delete the top and bottom tray of on screen.  That made the navigation buttons visible.  But there , surely ought to be a better solution.  

Stuck at installation,

Markux

---

### Post by MartynT on 2007-06-03
Hi Mark,

I had the same problem.  A dialog designed for 1024x768 on a 800x600 screen and the buttons off the bottom of the display.

The solution I used was to move the dialog up using <ALT>Left Mouse Button.

Other people have reported that they've had to use other buttons, but it does allow you to install.

[http://ubuntuforums.org/showthread.php?t=450519&highlight=screen+resolution]("http://ubuntuforums.org/showthread.php?t=450519&highlight=screen+resolution")
[http://ubuntuforums.org/showthread.php?t=456835&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=456835&highlight=resolution")

Good luck.

---

### Post by Wherdgo on 2007-06-06
> **markux said:**
> Since this happens during installation it makes the process very difficult; the major navigation keys at the bottom of installation screen is hidden and installation must be abundant.  I am curious to know that if this issue is a bug and a general problem how do other user go around it and install the system.  I have tried to remedy this by hiding and delete the top and bottom tray of on screen.  That made the navigation buttons visible.  But there , surely ought to be a better solution.  

Stuck at installation,

Markux

I think these are related vid issues, but different problems.  I've had both.

For the installation screen resolution problem, (Alt+ left mouse drag) it's still a known bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442)

For the persistent video issue after installing, try "sudo dpkg-reconfigure xserver-xorg" to re-write the config, use the existing defaults, and make sure your vertical refresh range is specified correctly.  Then reboot after completion.  I don't remember where I saw this tip, or I'd give them credit, but it worked for me.

---

