---
title: "Maverick dual monitor setup with one rotated on ATI graphics card"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by zeus77 on 2010-11-10
Hi,

I have a dual monitor setup with an ATI Radeon HD 5450 graphics card and the stock 8.78.30 fglrx driver.  In the ATI Catalyst Control Center, I'm operating with the "Multi-display Desktop", and all works great.  I've got one giant virtual desktop that's 2970x1680.

Now, here's where it gets weird.  This problem didn't exist in Ubuntu 9.04, 9.10, 10.04, so it's new to Maverick 10.10.  I want the left, secondary monitor to be rotated 90 degrees.  So, I go into Catalyst, and choose its rotation to be "right" instead of "normal".  It rotates immediately with no reboot required, and all works great... until I restart the X server, that is.  Once X is restarted, the whole system hangs.  It doesn't matter if I simply log out, reboot, or hit Ctrl-Alt-Backspace.  Any of these mechanisms for restarting X cause the whole system to hang.  And there's NOTHING in the log files.  I've checked /var/log/syslog, /var/log/xorg.0.log, etc.  

In order to get the system going again, I have to boot up through the command line, and change the rotation back to "normal" in /etc/X11/xorg.conf.  Then it works fine.  Again, to summarize:

> Dual monitor with both on "normal" orientation --> works fine.

Dual monitor with one rotated --> works fine immediately after setting rotation, but crashes on next X restart.

Anyone have any ideas on how to troubleshoot this?  I cannot find information in the log files anywhere... and it's 100% repeatable.

Thanks,
zeus77

---

### Post by spargonaut on 2010-12-04
hey zues, did you ever figure out a fix for this?
I'm running into the same problem.

while I'm happy to work this way until I need to restart (or logout), I'm sure it will become tiresome quickly.

---

### Post by spargonaut on 2010-12-08
For anyone interested, here is the work around i've been using so far....

method 1:
using the Catalyst Center, configure your monitors how you want them set up EXCEPT for the rotation.
As root (or sudo),
- in the directory /etc/X11
- make a copy of xorg.conf
     (I called mine xorg.conf.step)
After you do that, go ahead and rotate the screen using the Catalyst Center.
Before you reboot, copy xorg.conf.step back to xorg.conf
When your machine comes back up, you only need to rotate the orientation again.  Also, if you forget to copy xorg.conf.step back to xorg.conf (and your system hangs while booting), you can just boot into recovery mode and do the copy, then reboot again do the rotation.


method 2 (no command line):
After configuring your screens using the Catalyst Center, just make sure to rotate your screen back to a normal rotation before rebooting.  Just like method 1, you will have to re-rotate your screen after the system comes back up.

my additional $0.02:
Even if you use method 2, I would still go ahead and make a copy of xorg.conf (before you rotate) for those times that your forget to set the orientation back to normal before you reboot.

I'm not claiming these are the _best_ or _easiest_ methods, they're just what I do.  If anyone else has any suggestions or methods, I'm more than happy to entertain them.  These workarounds, while not all that difficult, are still annoying.

---

### Post by pro1 on 2010-12-17
Hi,

I had the same problem. Also tried to get a new version of the ATI driver from AMD, but it didn't work (side effect was a chaos of deb-packages and non-deb-stuff I had to "repair"). At the end I got this setup running simply by using the opensource driver, which I didnt expected ... maybe you try that to...

Best regards,
pro

---

### Post by zeus77 on 2010-12-19
spargonaut,
That's basically the exact same workaround approach I've been employing.  I still can't find anything in the log files, but I guess it's pretty clearly a driver issue.  What a pain...
zeus77

---

### Post by zeus77 on 2010-12-19
If you experience this bug, I encourage you to indicate this by clicking "Does this bug affect you?" at the top of the bug report here -- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/683905](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/683905)

---

### Post by spargonaut on 2011-01-31
dang.  didn't notice there were responses for this.  perhaps I should check my profile settings. hrmph.

@Zeus:  I haven't had too big of an issue with it, mainly b/c I rarely reboot, although its gotten me a couple of times.  what I have gotten, is really good at maneuvering the mouse with the monitor turned sideways (without tilting my head :D ).

@Pro1:  yea, i tried the open source driver.  several times.  Once I realized the issue with the ATI driver, I even tried some more.  It kept logging me out every time I would hit apply after I rotated the monitor (at least, i believe thats where it was logging me out.  sry, its been a while and I'm not at that machine right now).

_Specifically_, what did you do to get the open source driver to work?  which video port off the card is the rotated monitor hooked up to?  which build of the driver are you running?  etc.  The more details the better, please.

---

### Post by colinmccubbin on 2011-02-11
Since you guys are talking about 10.10 and dual head system(s) I hope you will excuse me crashing in to this thread...

I used to run dual monitors, one rotated, on an old box under winXP. I wrote web related code on the rotated screen, had the same page displayed 'in browser' on the normal screen..

I've really missed this over the last few months after saying to myself 'time to go 100% Open Source', never got it working on a dual boot 9.04/winXp   It is the only problem I have now running Ubuntu. I've found OS progs that do pretty much everything I was doing under winXP  ) But I'm getting very frustrated only having one screen.:(

My question, is this, if I start from scratch, new computer etc, what hardware (if any) would you recommend that WILL WORK with 10.4 or 10.10 to give me dual screen, rotatable  functionality 'out of the box'?

Thanks for your thoughts,

---

### Post by zeus77 on 2011-03-09
To the best of my knowledge, any modern graphics card (Intel, AMD/ATI, NVIDIA) will work.  Some may require you to disable desktop effects.  Some will have quirks like the one that inspired this thread.  The answer to your question is not a simple one since it varies for different models of cards and different versions of Ubuntu.  For example, my ATI Radeon HD 5450 worked fine "out of the box" until recently.  I expect it will again work fine out of the box once this bug is fixed in a future driver or version of Ubuntu (hopefully 11.04!)...

Also, I asked a similar question myself awhile back.  See here --
[http://ubuntuforums.org/showthread.php?t=1499137](http://ubuntuforums.org/showthread.php?t=1499137)

---

### Post by spargonaut on 2011-04-02
colinmccubbin,

yea, i forget exactly what video card that machine is running, but I know its an ATI card.  I was unable to get the FOSS driver to work with one screen rotated, and with the proprietary ATI driver, I have to implement the work around I described above.

If you're able to find a card/driver that can do this 'out of the box' please fill us in.

I use my rotated monitor for the same thing, programming and I won't lie, I'm pretty dang spoiled.

---

### Post by BradNeuman on 2011-10-17
I had the exact same problem with the HD 3450, but the problem went away when I upgraded to natty.

---

