---
title: "Out of Range - on installation 11.4"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by SliderTech on 2011-08-23
I was running v10x with no problems and then finally decided to upgrade to 11.4.  I did the up grade and had an error of "Out of Range"  I ended up doing a fresh install of 11.4 and I still get the "out of range". 

Because I have no terminal window I can not input any commands.  I have used 2 other monitors and still "out of range".

What can I do to fix this?

Thank you

---

### Post by dino99 on 2011-08-23
maybe check the free space on the partition(s)

---

### Post by SliderTech on 2011-08-23
Unfortunately I cant get by the "Out of Range" window.  No mouse or keyboard displaying on the screen.
The hard drive is new and it's a fresh install.

I read some other threads about this and they don't work for me, no terminal window to enter a command.

---

### Post by SliderTech on 2011-08-23
**I am reporting all this in hopes Someone can get an idea of what is going on.**


I rebooted and tried the "enter" and waited and nothing happened.
rebooted, waited 5 min then pressed enter and it changed screens and it displayed (initramfs) with a blinking cursor.

Other threads gave some commands to try, so here is what I get:
(note  "=" means result of that command)

ctl alt + does not do anything.
"reset xorg.conf:" = clears the screen and goes back to (initramfs).
"sudo rm /etc/X11/xorg.conf" =  /bin/sh: sudo: not found.
"rm ~config/monitors.xml" = rm: can't remove '//config/monitors.xml': No such file or directory.
"sudo dpkg-reconfig -phigh xserver-xorg" = /bin/sh: not found

After this I typed "exit" 
it went to a black screen with a mouse cursor. Then the desktop showed up.
It asked to to change to an NVIDIA accelerated graphics driver (version  current) (recommended) wanted password and then it installed and wanted a  reboot.
I rebooted and went to the "Out of Range" again.
I waited 5 min again then pressed enter. It went to the (initramfs) and  blinking cursor again. I tried the "reset xorg.conf:" & "rm  ~config/monitors.xml" with the same results as above.
I typed exit and it went to the desktop again.

I have gone into the monitor preferences and it's set to 1440x900  (16:10), I have changed it to 1024x768 (4:3).  (60Hz and rotation  normal)
It wont auto detect the View Sonic VA1703wb monitor. (it should, the v10x would detect it).

The monitor displays a window saying to adjust it to 1440x900 for best result.

I have gone into the additional drivers window and the NVIDIA accelerated graphics driver is activated but not currently in use.

I saved the adjustments as default. I rebooted and same Out of Range comes up.

I waited and hit enter went back to the (initramfs) and blinking cursor.  I typed exit and I got the desktop again.
The auto display comes up and says to adjust it to 1440x900.

I have now removed the proprietary drivers and rebooted.  Same problem.

I am now back at desktop and running the update manager and installing updates.

The screen just went to a white screen and it's not responding to mouse or keyboard input. 
Ill wait for a while and see if it still installs the updates.

Back later with results.

---

### Post by SliderTech on 2011-08-23
After the updates it came up with "failed to download package files" and now the network connection died for the package. It will go on line but wont connect to get packages.

I am so tired of dealing with this.

---

### Post by SliderTech on 2011-11-23
Sorry, I forgot to close this.

It seams no one could help me so I ended up just rebuilding the drive from a clean install with Ubuntu CE.

So the solution was to Rebuild it.

---

