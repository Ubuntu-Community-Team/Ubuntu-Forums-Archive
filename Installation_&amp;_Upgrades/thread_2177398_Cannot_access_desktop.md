---
title: "Cannot access desktop?"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by Warrior4Christ on 2013-09-28
Hey everyone,
I recently updated from Ubuntu 12.04 to Ubuntu 12.10.  When it was finished updating, I restarted my computer.  Everything was working fine and dandy, until it came to rebooting.  It rebooted normally at first, then the backlight shut off and the screen was totally black and not responding to anything.  I rebooted a few more times, and a screen reading "Ubuntu 12.10 thinkpad-ThinkPad-T43 tty2" appeared and asked for my password.  The password was not correct, but I was able to reset it.  I can now log in, but it just looks like command line.  I can't access my desktop.  Any advice?  Also, would putting the 12.04 ISO files on a flash-drive and booting from that help?

Thanks!

---

### Post by TheFu on 2013-09-28
a) what do the log files show?  Always start there.
b) if you've updated to 12.10 - don't use 12.04 files anymore.
c) newer is not always better. check my signature for why most people should run an LTS like 12.04.  Plus, 12.10 is not supported any more (or won't be in a month).

I bet the log files will tell us something useful.  Probably related to a GPU driver.

---

### Post by Warrior4Christ on 2013-09-28
How do I view the log files without being able to access the desktop?

---

### Post by TheFu on 2013-09-28
> **Warrior4Christ said:**
> How do I view the log files without being able to access the desktop?

Here's something funny ... I don't know how to access the log file FROM a desktop. I guess there's a point-n-click method?

I always open a terminal. ;)
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) explains.

---

### Post by Warrior4Christ on 2013-09-28
Ok, so I ran the first command, and the screen filled with stuff like this:

/var/log/Xorg.0.log:[    16.852] (WW) Warning, couldn't open module fglrx

There were about 15 more lines almost identical to that, except words like "ati, vesa, modesetting", and "fbdev" were sometimes in the place of "fglrx"

---

### Post by TheFu on 2013-09-28
fglrx is the proprietary ATI/AMD GPU driver.  Whenever a new kernel gets installed, you may need to reinstall and re-initialize this driver.

Try this:```

sudo apt-get  --reinstall install fglrx
 export DISPLAY=:0
 fglrxinfo
```

Then reboot.

---

### Post by Warrior4Christ on 2013-09-29
Ok, when I run the first command, an error message appears:

"Some packages could not be installed.  THis may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help you resolve the situation:

The following packages have unmet dependencies:
fglrx : Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages."

---

### Post by TheFu on 2013-09-29
By chance, did you install any .deb packages directly or add any PPAs?
Scratch that ..... 
Try 
[B]sudo apt-get --reinstall install fglrx
[/B]
I doubt it will work,but that seems to be the issue.  Are you ok without a GUI for a little bit? Comfortable in the shell?

---

### Post by Warrior4Christ on 2013-09-29
Hmmm....yet another error message:
[B]
E: Command line option 'r' [from -reinstall] is not known.
[/B]
BTW, thanks for helping me with this!

---

### Post by Warrior4Christ on 2013-09-29
OK, so I booted into tty1, and a notification came up saying that Ubuntu 13.04 was available, and that I could run **do-release-upgrade **to upgrade to it.  Should I upgrade, or would it mess my computer up even more?

---

### Post by TheFu on 2013-09-29
dash - dash - ... two of them.  Not 1.
If you are running 12.10 - yes, you should update to 13.04.
If you are running 12.04 - NO, you should wait for 14.04 to update and always, always, always run an LTS release.  IMHO.

---

### Post by Warrior4Christ on 2013-09-29
So, should I solve the blank-screen problem and then update, or before?

---

