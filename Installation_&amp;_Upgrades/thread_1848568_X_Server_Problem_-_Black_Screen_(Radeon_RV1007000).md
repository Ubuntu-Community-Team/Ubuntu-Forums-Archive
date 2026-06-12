---
title: "X Server Problem - Black Screen (Radeon RV100/7000)"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by svtguy88 on 2011-09-22
Ok,
I'm at about my wits end here. I can't, for the life of me, get X to come up on my new box. It's a Dell PowerEdge 1800 (2x3.0 Ghz, 2GB, ATI Radeon 7000M/RV100).

The Debian install CD brings up a GUI, as does the most recent Ubuntu Live-CD. I have KMS enabled, and have radeon specified in my xorg.conf file.

What's strange, is that Debian didn't install X by default, I had to use aptitude to do it. Also, there is no "startx" command, it is simply "X," which I also haven't seen before.

When I run "X," the monitor switches to where the X server should be running, but the display is just black. I have to switch back to tty to ctrl+c to get the system back. I've tried "fbdev" as the drive as well, but it gives the same result. If I try to run "xrandr" it says "Can't open display :0"

I have attached dmesg, xorg.log and xorg.conf. Any help would be greatly appreciated.

---

### Post by MAFoElffen on 2011-09-23
> **pkmgarf said:**
> Ok,
I'm at about my wits end here. I can't, for the life of me, get X to come up on my new box. It's a Dell PowerEdge 1800 (2x3.0 Ghz, 2GB, ATI Radeon 7000M/RV100).

The Debian install CD brings up a GUI, as does the most recent Ubuntu Live-CD. I have KMS enabled, and have radeon specified in my xorg.conf file.

What's strange, is that Debian didn't install X by default, I had to use aptitude to do it. Also, there is no "startx" command, it is simply "X," which I also haven't seen before.

When I run "X," the monitor switches to where the X server should be running, but the display is just black. I have to switch back to tty to ctrl+c to get the system back. I've tried "fbdev" as the drive as well, but it gives the same result. If I try to run "xrandr" it says "Can't open display :0"

I have attached dmesg, xorg.log and xorg.conf. Any help would be greatly appreciated.
I don't see anything in your logs that stand out as a show stopper!!!

Please refer to my sticky:
[[IMG]http://ubuntuforums.org/images/buttons/firstnew.gif[/IMG]]("http://ubuntuforums.org/showthread.php?goto=newpost&t=1743535")                          **[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
It may have a lot of reference that may help you.  (It is also good to refer to if I ask you something and you need more instructions or a translation.)

First question would be what version of Debian did you install?  

First comments would be that Debian "does" install the desktop as a default, so there may have been a "suspect" install error.  You said you corrected it by a manual install, but didn't say "what" you package you installed manually.

I try to help people resolve Graphics Issues. Most of my experience is universal to both Linux and Unix, as it relates to a boot loader, the kernel, Xorg, opensource drivers  and vendor's proprietary drivers.  With some info from you, hopefully we can work your issues out.

---

