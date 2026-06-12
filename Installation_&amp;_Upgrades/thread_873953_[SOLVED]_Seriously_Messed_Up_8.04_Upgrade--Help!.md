---
title: "[SOLVED] Seriously Messed Up 8.04 Upgrade--Help!"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2008-07-29
My system is getting stuck part way through the 8.04 upgrade, and I may not have the new sysctl.conf installed.  Is there any way I can get out of this mess?

I started an up upgrade from Gutsy to Hardy on my office machine and tried to finish it remotely from home .  The system likely uploaded all the software.  To install it, I rebooted the machine and tried to run the Update Manager via ssh -Y.  I couldn't get Update Manager to start, so I tried running sudo dpkg --configure -a.  I didn't know what I was doing and failed to tell it to upgrade sysctl.conf.  When dpkg was done, I could run Update Manager, but it gets stuck on localedef (so badly stuck I couldn't kill -9 out of localedef).

Could I transfer the sysctl.conf from my other 8.04 system (which has been running for some time) to the troubled computer?  Any way to fix the update?

Peter

---

### Post by pytheas22 on 2008-07-29
I'm not sure if it will help, but you can burn an alternate CD, which also allows you to upgrade your system.  To download the ISO, go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and make sure to check the box that says, "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

I'm not positive if the system-upgrade utility on the alternate CD will be able to fix your problems, but it probably can't make things worse than they already are.
> 
Could I transfer the sysctl.conf from my other 8.04 system

In principle you may be able to copy a different sysctl.conf over--I don't think that file says many things on Ubuntu anyway--but I'm not sure how much that would fix, as I suspect that your problems lie deeper than sysctl.conf.

---

### Post by slowtrain on 2008-07-29
Hi pytheas22:  Thanks for the suggestion, it looks like a helpful one in a bind!  As it turns out, I seem to have done an end run around the problem.

For anyone else who foolishly thought that it might be ok to reboot between downloading the 8.04 upgrade software and actually installing it, here's how I got around the problem:

Update Manager won't work.  What you can do is add your location (click on the calendar link in upper right corner next to the power button, then click the small location rectangle and click the edit button).  This prevents it from getting into an infinite loop when setting up locales--right about here:

Setting up locales (2.7.9-4) ...
Generating locales...
 en_AU.UTF-8...

After setting your location, run (from the terminal window):
sudo dpkg --configure -a

Peter

---

### Post by slowtrain on 2008-07-29
Oh, and I also needed to reboot a couple times to stop my software from crashing after the update.  So far, it looks stable after this.

---

