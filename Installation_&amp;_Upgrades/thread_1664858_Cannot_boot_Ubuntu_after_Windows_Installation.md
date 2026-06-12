---
title: "Cannot boot Ubuntu after Windows Installation"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Guidobot on 2011-01-11
Followed the instructions for the Windows Ubuntu Installer (10.10). Used defaults for install. Howeevr, after PC restarted I do not get the option to boot Linux but go straight in to Windows. (I think this means GRUB doesn't start?)
 
What do I do?
 
I'm running XP on a AMD Athlon 64 PC.

---

### Post by chris0108 on 2011-01-11
As i read that you have installed ubuntu in windows, ie wubi, so there wont be the option to boot 'into' ubuntu you access it when booted in windows like a normal program would be

---

### Post by Rubi1200 on 2011-01-11
Hi and welcome to the forums :)

For Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It seems you have problem #2, but did you apply any updates or did this happen immediately after the install?

---

### Post by Guidobot on 2011-01-11
Thanks for the reply Rubi1200.
 
Problem#2 appears to apply from the Wubi megathread. However, the solutions are confusing. I have a brand new 10.10 install as opposed to the upgrades discussed.
 
I used the direct Wubi installer that appeared to reserve space on my main C: (Windows) partition. (Indeed I can't manually split this partition under XP as demonstrated in the YouTube videos.)
 
These solutions also refer to a LiveCD. I have burnt a 32-bit version of the Ubuntu .iso file onto CD. Should my next move be to try to install from this? If so, do I need to use the Wubi uninstall first or will I be able to use this to force a boot with my current Wubi install?
 
Oh, and I applied no updates after the Wubi install. This happened immediately afterwards.

---

### Post by bcbc on 2011-01-11
For some reason the Wubi installer doesn't always successfully add an entry into the Windows Boot Manager (boot.ini on XP). It's not clear why this doesn't always work.

Sometimes the entry is there but the "timeout" setting remains at 0, therefore there is no prompt and it boots instead straight into Windows.

So that's where you need to look. Post the results of the hidden file C:\boot.ini and this will likely explain the problem.

(At this point, Ubuntu has not yet been installed - just the virtual disk (unformatted)and swap file have been created).

If you want to know how to view/edit the boot.ini - this is how microsoft recommends [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by Guidobot on 2011-01-11
> **bcbc said:**
> For some reason the Wubi installer doesn't always successfully add an entry into the Windows Boot Manager (boot.ini on XP). It's not clear why this doesn't always work.

Sometimes the entry is there but the "timeout" setting remains at 0, therefore there is no prompt and it boots instead straight into Windows.

So that's where you need to look. Post the results of the hidden file C:\boot.ini and this will likely explain the problem.

(At this point, Ubuntu has not yet been installed - just the virtual disk (unformatted)and swap file have been created).

If you want to know how to view/edit the boot.ini - this is how microsoft recommends [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

Thanks a bunch bcbc.

This was EXACTLY the problem and fix I needed. I figured it was something to do with the start-up delay but didn't know how to change this. In fact it is as simply as a check-box enable.

For anyone else with this (XP) issue try:
MyComputer->(R-click) Properties->(Tab) Advanced->(Settings) Startup and Recovery->(Check) Time to display list of operating systems [30]

---

### Post by Rubi1200 on 2011-01-12
Excellent! Glad you got it sorted out and thanks, too, to bcbc for pointing you in the right direction.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

