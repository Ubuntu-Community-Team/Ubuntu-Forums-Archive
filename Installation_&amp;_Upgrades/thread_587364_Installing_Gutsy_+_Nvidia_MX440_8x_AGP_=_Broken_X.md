---
title: "Installing Gutsy + Nvidia MX440 8x AGP = Broken X"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by DemonicKyle on 2007-10-22
Finally finished installing Gutsy using a network install.  Rebooted, and X dumped out the error that my Nvidia kernel version didn't match my X version.

So I tooled around on these forums, looking for clues.  I've been at it for a few hours, and now my error messages have changed, but still no X, no desktop.

Currently, on attempting to start X, I get the following:

```
...
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
(II) Module already built-in
FATAL:  Error running install command for nvidia
(EE) Nvidia(0):  Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining


```

So, all in all, I have no idea what's going on.  My abilities at fixing X are extremely limited - something similar to this happened last year when I attempted to upgrade my video drivers, and it took days of tooling to fix it, and I don't even know what I did. 

Any help would really be appreciated.

Thanks,

-DK

---

### Post by Pumalite on 2007-10-22
To compile a driver for your card into the kernel you need kernel-headers matching your kernel and build-essential.

---

### Post by Pumalite on 2007-10-22
If you have finished your installation and ended up with a blank screen:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by DemonicKyle on 2007-10-22
Ok, did that, after 'startx', monitor goes into standby, all dark.  I hear my harddrive working hard though, and I think it boots into the desktop....I just can't see it.

Able to see some output after hitting Ctrl-Alt-F2.

I see this error:

(EE)  Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Any more ideas?  I'm getting pretty desperate here...

-DK

---

### Post by bruban on 2007-10-22
DK,

Something out of left field:

Is your monitor an LCD and connected to your PC via a DVI cable?

If so there does appear to be an issue with this combination.

Assuming that this is the problem, try connecting to your monitor with the VGA DSUB cable to see if that makes a difference on reboot.

---

### Post by DemonicKyle on 2007-10-22
Problem solved, following this:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg424804.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg424804.html)

Cheers,

-DK

---

