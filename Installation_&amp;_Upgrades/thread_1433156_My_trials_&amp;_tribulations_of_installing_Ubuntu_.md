---
title: "My trials &amp; tribulations of installing Ubuntu 9.10. There is hope!"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-03-18
This isn't a question but an observation. 

I thought I'd pass along my trials & tribulations of my recent install of Ubuntu 9.10 with nVidia video graphics. I do this with the thought it might help someone with similar install issues. Administrator, please relocate this post if deemed needed.

First a disclaimer. I know little about computers so many of my observations are from a novice point of view. When I have an issue I do read many forum posts hoping to find a clue how to solve my issue. But one can't read them all so what I am saying may have been posted elsewhere. Sorry, if that is the case.;)

I wanted to install Ubuntu 9.10 from the Live CD on a PC with an Intel 2.66 Core2 with 4Gb RAM, nVidia 6800GT Graphis card & 3 large HDDs; one with WinXP Home installed.

Everything about the install seemed normal until needing to restart the PC. Instead of booting to the desktop it slowly arrived @ a terminal-like screen that says *Ubuntu 9.10 tty1* & prompts for user name, then password. Weird, so I re-booted. Got this again. Then I re-booted to GRUB & selected Recovery Mode. Got to a menu & selected DPKG repair. It loaded 160Mb of data & installed. Re-booted & once again it booted to *Ubuntu 9.10 tty1* & prompts for user name, then password.

On another PC I read that there were lots of issues wit nVidia graphic cards so I thought installing the proper driver might help. So, booted to *Ubuntu 9.10 tty1* & got to the terminal & did *sudo apt-get update* & *sudo apt-get upgrade* but everything was @ 0. Found 2 nvidia drivers available & installed the highest offered - v173. But upon restarting I still got *Ubuntu 9.10 tty1* & prompts for user name, then password.

This time I shut it completely down, read some more from this forum, found a suggestion. Booted the PC to try the suggestion only this time it booted to the *desktop*! But, some features didn't work so I posted ([http://ubuntuforums.org/showthread.php?t=1431266](http://ubuntuforums.org/showthread.php?t=1431266)) & after 4 pages my friend *spyrule* suggested to re-install 9.10. I tried the Live CD but if failed to boot to the install screen. Then I tried to boot the live CD to it's desktop & that failed, too (BTW- I did check the disc before installing). Finally, I burned a new DVD install disc.

It booted normally to the install section but I felt uncertain & had some questions about install point so I aborted. Once I got answers, I booted the DVD install disc only to be greeted with the same failed boots as the Live CD! After several attempts, I shut down; took a break.

About 30 minutes later I tried again & everything worked. Install when great & restarted the PC. It promptly booted to *Ubuntu 9.10 tty1* & prompts for user name, then password again! 

But, this time there was no panic. I seemed to see a pattern here. I shut it down. Waited 30 minutes & boot again; this time to the desktop like everything was normal! Check a few things & unlike the 1st install, all was normal this time around. Did the necessary update & upgrade. The system downloaded & installed 240mb of date to complete the install. I did not install nVidia drivers at this time because I noticed in GRUB the kernel was 2.6.31-14 when I booted & knew 2.6.31-20 was just installed & would not take effect until I restarted my PC. I wanted 2.6.31-20 to be active when installing the new nVidia driver. So, time to restart.

To absolutely no surprise it booted to *Ubuntu 9.10 tty1* & prompts for user name, then password. Shut it down & applied the 30 minute rule. 30 minutes later it booted perfectly to the desktop. Installed the best nVidia driver offered, v185, & restarted - this time perfectly to the desktop; & it has booted perfectly every since.   

The question that remains is why did it need a 30 minute rule? I have a theory. It is a memory issue but I'm not sure if it is system RAM (4Gb) or video graphic RAM (the nVidia 6800GT has 256mb of video RAM). But, at this point the system is running on a generic video driver which must be relatively small & easily over saturated. 

After new  install, RAM is still somewhat saturated as it only shuts down to a point, then booting starts & it has insufficient memory to boot to the desktop, so it goes to the terminal screen. But, after a complete shut down, the memory has cleared after the 30 minute rule & it has has enough to boot to the desktop.

Chime in if you care to. All I know is the 30 minute rule worked without issues whereas nothing else did. Just need to pamper it a bit.;)

---

