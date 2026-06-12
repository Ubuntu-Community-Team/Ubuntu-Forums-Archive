---
title: "White Screen of Death"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Darkhack on 2009-07-30
Ubuntu 9.10 Alpha 3 installed just fine and I can boot into it.  The desktop runs fine for about 60 seconds (I can open applications, move around, etc), but then I get a white screen of death.  The entire screen turns white and everything is locked.  I can't do ctrl-alt-F1 to get to a terminal.  Even when I press Num Lock on my keyboard, the light doesn't change.  I have to do a hard reboot.

I've had this problem before when I was using 8.04.  The solution was to remove powernowd.  I'm on a desktop, but for some reason powernowd would be running.  The problem I'm having with Karmic is the exact same I initially had with Hardy.  However this time, I see no powernowd to remove.  It's not installed at all in Karmic.

I figure there must be an equivalent program.  Does anyone know what it is?  Anyone else ever had this problem?

Edit: [Here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/46470").  It actually dates back to Dapper.  As you can see, myself and others have all fixed the problem by disabling powernowd.  It's just that Karmic no longer uses it, so there must be another equivalent daemon running.

Edit: I've found a solution.  The new name for the CPU frequency scaler is ondemand.  Here is how to disable it.
1. sudo apt-get install rcconf
2. sudo rcconf
3. Scroll down to 'ondemand' and disable it.  Then reboot.

---

### Post by camper365 on 2009-07-30
I've seen this happen before. However, it only happened once or twice and never again. It seems like your problem is much more severe than what I had. Only when I had my problem, it would change colors, going from darker to lighter, eventually hitting white, then back down until it almost hit black. I ended up doing a hard reboot after a while, but this is when I was having problems with GDM not starting properly. I purged GDM and reinstalled it, and GDM worked fine, but it doesn't sound like that's your problem. I think that ubuntu-desktop had to be remove in order for gdm to be purged. You could try purging that and reinstalling it.

---

### Post by philcamlin on 2009-07-30
do you have the correct videro drivers installed?

---

### Post by wayne_cat on 2009-07-30
check the log files:

- /var/log/syslog
- .xsession-errors

start "top" in a gnome-terminal ... maybe a process is running berserk.

---

### Post by Darkhack on 2009-07-30
It's not a video card problem.  The issue occurs regardless of the drivers I'm using.  It happens with ati, fglrx, and vesa.

The issue is with a particular feature of AMD processors which have something called [Cool'n'Quiet]("http://en.wikipedia.org/wiki/Cool%27n%27Quiet") which was controlled by the daemon process powernowd.  However that daemon process no longer exists in Karmic.

I believe it's because DeviceKit is replacing it.  However I can't simply remove all of DeviceKit, so I need a way to disable just this particular feature.  I suppose I could boot with acpi=off, but I'd like to be able to put my system into sleep mode.

I was just wondering if anyone happened to know the quick solution off hand.  If not, I'll ask on DeviceKit's mailing list.

---

### Post by alphacrucis2 on 2009-07-30
> **Darkhack said:**
> It's not a video card problem.  The issue occurs regardless of the drivers I'm using.  It happens with ati, fglrx, and vesa.

The issue is with a particular feature of AMD processors which have something called [Cool'n'Quiet]("http://en.wikipedia.org/wiki/Cool%27n%27Quiet") which was controlled by the daemon process powernowd.  However that daemon process no longer exists in Karmic.

I believe it's because DeviceKit is replacing it.  However I can't simply remove all of DeviceKit, so I need a way to disable just this particular feature.  I suppose I could boot with acpi=off, but I'd like to be able to put my system into sleep mode.

I was just wondering if anyone happened to know the quick solution off hand.  If not, I'll ask on DeviceKit's mailing list.

Probably best to report the problem on launchpad.

---

