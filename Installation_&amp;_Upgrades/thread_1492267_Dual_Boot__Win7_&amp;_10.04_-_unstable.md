---
title: "Dual Boot  Win7 &amp; 10.04 - unstable"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by CNBarnes on 2010-05-24
Does ANYONE have a stable dual boot Win7 & Ubuntu 10.04 system?

I have been trying for WEEKS to get a computer configured for my student lab.   I get things going and everything seems to work for a few days.   And then for no reason, the next time I reboot, Grub just seems to commit suicide.

Latest example.  
Win 7 & Ubuntu have been co-existing perfectly fine for about a week.  Iow, I do something, then reboot, and the grub menu comes up - I select something and it boots my OS of choice for that session.


But today, I've been putting the last few touches on this computer before I use Clonezilla to copy it to all of the computers in the lab.   You know - hard stuff like:
* set the default profile in Windows
* install a printer in both Ubuntu & Windows
* set a background image for the logon screens that have our "don't do anything bad" policy.

See how there is nothing in there that should mess w/ grub or the boot loader, right?

Yet I reboot the computer, I get to where grub should load - and BARF - I get the Bios splash screen again and the computer reboots on it's own.


I'm going to TRY to use the stuff in 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475646](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475646)



but my immediate question is:  [B]What the !@(#$&!@#$% is going on that this keeps happening to begin with?  :confused:

[/B]

---

### Post by oldfred on 2010-05-24
Its windows software that wants to hide serial numbers or settings into space not normally used by the windows boot loader in the MBR. But grub2 is slightly larger and that is just enough to cause part of grub2 to get overwritten. The MBR is supposed to be reserved for booting - Master Boot Record. So to me it is one more thing windows does that is not right.

---

### Post by CNBarnes on 2010-05-24
The good news is that the top section of this post:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

fixed my problem.   Still, it is annoying as hell.

---

