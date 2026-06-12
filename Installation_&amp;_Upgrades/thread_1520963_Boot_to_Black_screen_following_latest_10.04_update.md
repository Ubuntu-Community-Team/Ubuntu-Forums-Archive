---
title: "Boot to Black screen following latest 10.04 update"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by noodlemctwoodle on 2010-06-30
I have just installed the latest update for Ubuntu 10.04, however upon requested restart i now boot to a black screen. 
 
the boot sequence is system post, followed by the generic Purple UBUNTU loading screen, following that you just get a black screen. 
 
Unfortunately im a complete novice when it comes to ubuntu so any help would be greatly appreciated.. 
 
Many Thanks
 
AMD x64
4Gb RAM
120GB Intel SSD
ATI RAIDON 3650

---

### Post by stlsaint on 2010-06-30
Do you get any errors or anything? Is it a complete blank black screen or do you see lettering?

---

### Post by twgray on 2010-06-30
I am having a similar problem after a 10.4 64-bit upgrade.  My system stops at a blinking cursor after displaying:

Boot from (hd0,0) xfs
Starting up...

I can recover by selecting the recovery option in Grub, doing a Resume normal boot, logging in from command line, and then starting x, "startx", from the command line.  Maybe that will work for you until we find a solution.

---

### Post by samcoinc on 2010-06-30
I have had twice now using the driver packages from ati for my radeon mobile video card (4670 1gB) Black screen.  It gets to the point that the loggin screen should appear and boom - black screen.

Twice now I have uninstalled the ati drivers and went back to the open source ones.  (that is where I am at now) the drivers run great for a week or two then black screen.

(not to be confused with teh blinking curser after grub. which I get a good 50% of the time)

sam

---

### Post by sparty_xubunter on 2010-06-30
I have a similar problem (posted a thread on general help)

Mine boots to terminal and the xfce session won't start.

My current work around is not really a help.  I go to the grub menu and boot from the .22 kernell, then my xterm pops up.

---

### Post by BCollar on 2010-07-16
Hello,  I'm having the black screen after the Ubuntu loading screen also.  There's no cursor or any indication the computer is thinking.  

This comes after a pretty gutsy upgrade (I didn't back up or try a live cd first) from 9.10 Karmic Koala.

I'm lost as to what to do next.  What do you think might be the problem,  and how should I proceed?  Thank you ahead of time for any suggestions.  I'm fairly new to Ubuntu.  

My computer is a Gateway 7340,  pentium 4,  integrated graphics, with 512mb ram.  

Is there a way to recover the previous installation or save my data?  If I can't proceed with the Lynx upgrade.

---

### Post by kittkatt on 2010-07-17
I had the same problem.  I was able to solve it by uninstalling my ATI drivers (I had dloaded the latest '.run' file directly from the site) and switching to the one located in the "Restricted Hardware" section of the System tab.  

To get back into Ubuntu temporarily, use the recovery option at GRUB, then there is an option something like "use failsafe graphics".  Select that to get in.

---

### Post by colinpat on 2010-07-17
Same problem on my Acer Travelmate 660.  Live upgrade from a perfectly working 9.10.  On reboot just goes to black screen with no text no cursor.
No grub menu either so am stuck with what to do next - apart from go back to clean install 9.10.  Any suggestions would be greatly appreciated.

---

