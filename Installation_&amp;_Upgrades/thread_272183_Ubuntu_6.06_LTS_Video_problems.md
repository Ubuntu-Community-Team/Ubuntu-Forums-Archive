---
title: "Ubuntu 6.06 LTS Video problems"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by MainFrame185 on 2006-10-05
I have been using Debian Sarge for a while now. I use it in a server configuration and have several machines running PostFix, Asterisk, etc. I wanted to try a Linux desktop distro with a Gnome GUI to see if I can use it in a small business environment. I took the Linux Distro quiz and it reported that Ubuntu was the best choice based on my experience level, hardware, and applications I want to run. I downloaded the 6.06 LTG distro and burned the iso to a CD. When I boot the CD I get the Ubuntu splash screen and main menu. No matter what option I choose, an "Unsupported Video Resolution" error comes up shortly after the boot process begins, and that is as far as I can go. Here is my hardware configuration:

Dell Dimension 5150
2.8 GHz Pentium IV processor with dual core
1 GB RAM
128 Mb ATI RagePro Video Adapter (digital)

Any suggestions?

---

### Post by dcstar on 2006-10-08
> **MainFrame185 said:**
> I have been using Debian Sarge for a while now. I use it in a server configuration and have several machines running PostFix, Asterisk, etc. I wanted to try a Linux desktop distro with a Gnome GUI to see if I can use it in a small business environment. I took the Linux Distro quiz and it reported that Ubuntu was the best choice based on my experience level, hardware, and applications I want to run. I downloaded the 6.06 LTG distro and burned the iso to a CD. When I boot the CD I get the Ubuntu splash screen and main menu. No matter what option I choose, an "Unsupported Video Resolution" error comes up shortly after the boot process begins, and that is as far as I can go. Here is my hardware configuration:

Dell Dimension 5150
2.8 GHz Pentium IV processor with dual core
1 GB RAM
128 Mb ATI RagePro Video Adapter (digital)

Any suggestions?

Assuming that the message is actually coming from your monitor, you may try to switch to a text screen by pressing CTRL-ALT-F1 when it happens.

If it does switch, you may want to search for similar problems in the forum about setting another video mode.

---

### Post by smonsarr on 2006-10-09
Hi, I have the same PC with a Radeon X600 video card and a DELL 1707FP screen and the same initial problem as yours. 
When the PC boots up and the welcome screen appears notice the options at the bottom of the screen. 
[LIST]If you press F4 you can manually select the correct video mode (in this case 1280x1024x32) - this fixed the "Unsupported Video Resolution" error from the monitor (btw if you switch to analogical PC - screen connection you do not get this error - but a very ugly video image).[/LIST]
[LIST]If your keyboard is not US english, now is also the time to press F3 and select your keyboard.[/LIST]
[LIST]You cannot start the cd in normal mode (i.e. do NOT select the default "Start or install Ubuntu"), the xserver crashes on startup with a "device not found" error... 
You have to chose "Start Ubuntu in safe graphics mode".[/LIST]
This got the live CD working for me. I have not tried installing Ubuntu yet, (I am under FC5 for the moment and am thinking of swiching).
If you go ahead and install Ubuntu on this platform I would be VERY interested in your results.
__________________
Regards, Samuel.

---

### Post by smonsarr on 2006-10-30
Well I cannot get the live CD of 6.10 to boot AT ALL on the Dell Dimension 5150 ! :(
Whatever I seem to try xorg crashes saying that it cannot find the screen.

---

### Post by jbennet on 2006-11-07
i have the same machine nearly

dell 5150
1gb ram
P4 cpu with HT
ATI x600 graphics card

Some distros dont like this card - bootup and then you get a menu with a timer - it should have an option for "boot in safe graphics mode" - when x crashes do control-alt-f2 and use vi (readup on how to use it, its a command line text editor) to chage /etc/x11/xorg.conf so that the line which reads driver = radeon (in section video) reads "vesa" instead

---

### Post by scrofula on 2007-01-06
I tried the solution above but didn't know what to do next. How do I carry on the install process?

---

