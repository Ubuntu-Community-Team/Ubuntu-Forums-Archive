---
title: "Can't get into Ubuntu OR windows"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by Zeenomorph on 2007-07-16
I was trying to install Ubuntu on my laptop.  I was getting an Xserver error.  A member on this board (Thank you Merlin) advised me to get the alternate text based version of Ubuntu to get around this.  I did that.  

I hope that you're still out there Mr. Merlin!

I have now made a boot disk for the 'alternate text based' version.
I installed it. I think it's on my computer, but I can't tell.

Here's the situation now. I installed it to the point that the disk ejected and the computer rebooted. It came up as loading Ubuntu. I was very happy, and then, the same ****! All that Xserver stuff again. I typed into the command line the same thing that you told me to do last time. This time I get this message;

xserver-xorg postinst warning: overwritting possibly-customised configuration file, backup in /etc/X11/xorg.conf.20070715180334

Then i'm at the command line, and I have no idea what you type.

As a further problem, I can't seem to get into windows anymore, so now I'm effectively without a computer until this gets fixed. I reallly do want to use Linux, I have no desire to use Windows whatsoever, but I must admit that I am becoming frustrated. I just want to boot an operating system, and use my computer.

Anyway, if anyone out there in the Ubuntu community can get me through this snag so that I may begin to enjoy this software I'd be eternally grateful.

I'd even be happy if I could figure out how to erase everything I did so that I could start again, but when I put in a Windows boot disk it just stays at a black screen.  I have no idea what to do!

---

### Post by merlinus on 2007-07-16
> 
xserver-xorg postinst warning: overwritting possibly-customised configuration file, backup in /etc/X11/xorg.conf.20070715180334

Then i'm at the command line, and I have no idea what you type.


```

startx

```

-merlin

---

### Post by Zeenomorph on 2007-07-16
I'm sorry to say that that didn't get me anywhere.

Fatal server error:
    no screens found
XIO: fatal IO error (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed with 0 events remaining.

---

