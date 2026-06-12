---
title: "xdm problems"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by sry.noname on 2006-04-19
i've installed a minimal system using the server installation and then:
(apt-get update, universe repositorie enabled for xfce4)
apt-get install xserver-xorg x-window-system-core numlockx xterm xdm xfce4

the problem is, when rebooting xdm pops up for one or two seconds (just a grey screen and a cursor symbol is shown, not the login prompt), then it returns to the console - without any error/message.

(when i start xfm using sudo xfm it's the same, startx works fine and starts xfce4)

what am i doing wrong?
is there any error log which could help me?

---

### Post by draenor on 2006-04-19
Well, I'm currenty experiencing the same problem. I was beginning to think there was some error with my xdm installation. I'm just slighty to tired atm to scoure through the tons of man pages on xdm right now.
Btw /var/log/X.org.0.log is the closest related log file (non-existent xdm.log). Personally I can't find anything strange in mine, but perhaps you can in yours though.

---

### Post by sry.noname on 2006-04-20
hmm same problem here, nothing really intersting in this log, only some warnings, however by chance i found xdmshell which seems to start xdm too, it's also not working, but at least gives an output, see here:
[http://server3.pictiger.com/img/240149/picture-hosting/xdmshell-error.gif](http://server3.pictiger.com/img/240149/picture-hosting/xdmshell-error.gif)
**somebody can help us with this information?**

---

### Post by sry.noname on 2006-04-20
hey mate, this seems to be a bug of ubuntu 5.10 (the missing libXdmGreet.so). google for it if you need more. i'll change to gdm.

---

### Post by draenor on 2006-04-20
Yeah I'm googling for it, but it seems this is a known bug and other distributions (mainly debian) have had the same problem. 
There's always the unofficial package at [http://download.cmeerw.net/debian/xdm/source/xdm_0.99.1.orig.tar.gz](http://download.cmeerw.net/debian/xdm/source/xdm_0.99.1.orig.tar.gz)
I'm not sure this works though, I just unpacked it and it says I'm missing Xaw package, which should be part of x-window-system. 

There there's a script fix proposed by one of the debian maintainers. 
[http://groups.google.com/group/linux.debian.bugs.dist/tree/browse_frm/month/1998-11?_done=%2Fgroup%2Flinux.debian.bugs.dist%2Fbrowse_frm%2Fmonth%2F1998-11%3F&](http://groups.google.com/group/linux.debian.bugs.dist/tree/browse_frm/month/1998-11?_done=%2Fgroup%2Flinux.debian.bugs.dist%2Fbrowse_frm%2Fmonth%2F1998-11%3F&)

Then there's it seems possible to create a symlink in it's place, but xdm will return an "insecure session" message but will load. 

But still, I haven't found a good solution, so matter is still in the air.

---

### Post by draenor on 2006-04-20
Ok the source package I downloaded didn't seem to work too well, since it complained about missing X11, etc. Either way I missed there was a debian package right next to the link, which comes here

[http://download.cmeerw.net/debian/xdm/binary-i386/xdm_0.99.1-3cmeerw_i386.deb](http://download.cmeerw.net/debian/xdm/binary-i386/xdm_0.99.1-3cmeerw_i386.deb)

sudo dpkg -i <filename>

---

