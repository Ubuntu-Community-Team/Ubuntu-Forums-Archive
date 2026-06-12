---
title: "No X after upgrade to 7.04; wrong file name."
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by marcx on 2007-05-14
After upgrading from 6.10 to 7.04 (method: sudo apt-get dist-upgrade, yes, I know), I partially lost my graphical X-startup screen.
I can log in in text mode, though.
After typing 'startx', a gray dotted X-screen appears, and I can move the cursor. But nothing else happens.

Closing X with 'CTRL+ALT+Backspace, I receive the following error:* AIGLX: screen 0 is not DRI capable.*

I found out that I need to install xserver-xorg-video-savage. When installing this package with apt, the following error appears:

[I]dpkg: error processing /var/cache/apt/archives/xserver-xorg-video-savage_1%3a2.1.2-1_amd64.deb (--unpack):
trying to overwrite /usr/share/man/man4/savage_4.92, which is also in package xserver-xorg-driver-savage.

Errors were encountered while processing: /var/cache/apt/archives/xserver-xorg-video-savage_1%3a2.1.2-1_amd64.deb 

E: Subprocess /usr/bin/dpkg returned an error code (1)
[/I]

Of course the spelling of "video-savage_1%3a2.1.2-1" is obviously wrong: it shoud be spelled as "video-savage_1:2.1.2-1".

It seems that somewhere in the proces, some piece of software is not able to use the ':' in the name.

I tried to 'apt-get install xserver-xorg-video-savage_1:2.1.2-1_amd64.deb'. Same result, the ':' is translated into '%3a', the file cannot be handled.

I'm not sure wether the misspelling is the only cause of stopping the install proces, or wether the AIGLX-problem is the real problem.

Besides, there is a third error, that&#347; possibly related:
apt (or is it the system?) complains that it cannot find a bunch of font files in /urs/share/fonts/X11/, while the system thinks they are in /usr/share/X11/fonts.

System is AMD64. Ubuntu 6.06 ran flawlessly in this machine, and found the Nvidia on-board device NV 40 GEforce 6200 immediately. In the logs I see that the GEforce 6200 this time also is recognized. The driver 'nv' is loaded by xorg-conf.

Any suggestions?

---

