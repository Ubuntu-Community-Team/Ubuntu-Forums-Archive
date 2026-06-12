---
title: "Password quits working"
date: 2020-08-07
forum: Installation &amp; Upgrades
---

### Post by adam27530 on 2020-08-07
PC    Dell    M4800    Laptop

OS    20.04

Re-installed  OS three times

When I install the OS it completes successfully. Can log in with no difficulty. However after running 'sudo apt upgrade'
I can not log back into the system. I enter the password at the user prompt and the system promptly displays my user
id again.  I click on it and it prompts me for the password again. However if I enter a password that is not the right 
password the system seems to go into a delay routine, then displays the message, "Sorry, that didn't work, please try 
again". Um, which way do I go?

---

### Post by TheFu on 2020-08-07
Try:
```
sudo apt update && sudo apt full-upgrade
```
The update needs to happen within about 6 hrs of any attempted "upgrade" so dependent packages aren't out-of-sync.

Just a guess.

---

### Post by adam27530 on 2020-08-07
Thank you.

The norm is to run 'sudo apt update' then soon as update is done to run 'sudo apt upgrade'.  I will give   '[COLOR=#000000][FONT=&quot]sudo apt update && sudo apt full-upgrade' [/FONT][/COLOR] a whirl.

regards

---

### Post by CatKiller on 2020-08-07
> **adam27530 said:**
> I enter the password at the user prompt and the system promptly displays my user
id again.  I click on it and it prompts me for the password again. 

To save you from barking up the wrong tree any more, this has nothing to do with your password, and nothing to do with logging in. Something (likely graphics driver related) is causing your desktop environment to crash and the first thing that gets shown when it restarts is the login screen.

---

### Post by TheFu on 2020-08-07
For 20.04, a login loop was listed in the release notes as an issue. [https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)
> Systems with an nVidia graphics card: These systems boot the live session by default with the open source video driver 'nouveau'. On some hardware this driver may crash which results in a freeze of the graphical session of the installer. If it happens, on the boot menu, select a 'Safe graphics mode' entry. Then in the installer, on the 'Preparing to install ...' page, select 'Install third party software ...' and continue. This option will install the nVidia proprietary drivers on the target system. Upon installation the proprietary drivers for your card will be loaded and the graphical session should work properly with optimized drivers. (1871562) 

I've seen older systems where the user immediately ran **sudo gedit /etc/hosts** get stuck in a login loop.  On a 20.04 system, the issue cause doing that that shouldn't happen, but on older releases (for lurkers), it still can.

---

### Post by adam27530 on 2020-08-07
Well I installed the OS for a 4th time and this time instead of running off to get the WiFi up, then run update and upgrade I edited 
'grub' to default to the console outside the gui environment. What dropped me in the soup pot previously was the installation from 
the flash media worked and no login aggravators. The failure occurred after running update and upgrade. I am leaving it on over 
the weekend to see if all is golden Monday morning. If so I will try running update and upgrade, then discover if the process sur-
vives outside the gui.

---

