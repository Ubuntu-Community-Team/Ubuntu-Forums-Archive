---
title: "intel 950 w/external monitor display quality"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by apease on 2008-01-03
Hi!
  I have a Toshiba A205-S4777 laptop running an Intel 950 Graphic Media Accelerator video card.  I've installed Ubuntu 7.10.  The laptop screen is recognized properly.  I have a 22" ViewSonic monitor at 1680x1050 resolution.  Although I can get output at the resolution on the monitor, the image quality is very poor.  For example, with two adjacent "l" characters one will be pale and the other bright, as though the output resolution is not in fact 1680x1050 (however, I don't think that's it, since the monitor itself will complain if a different resolution is used as input, and it doesn't complain).  Has anyone experienced this?

many thanks,
Adam

---

### Post by apease on 2008-01-29
I think I may have some more relevant detail about the problem.  Occasionally on boot I get the message

There was an error starting the Gnome setting daemon
Failed to conect to socket /tmp/dbus-kjXMSdo875
connection refused

After this, the fonts and display are very nice.

Anyone have an idea about this?

many thanks for any responses
Adam

---

### Post by jrthom444 on 2008-02-01
Hi,

This may not help but you might wanna take a look at this.

[http://ubuntuforums.org/showthread.php?t=684185&highlight=Toshiba](http://ubuntuforums.org/showthread.php?t=684185&highlight=Toshiba)

---

### Post by apease on 2008-02-03
Hi,
  Many thanks for the reference.  I tried the instructions:

Fix:
Edit: /etc/gdm/gdm.conf
Replace:
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
flexible=true

WITH

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96
flexible=true

Reboot

But unfortunately that had no effect on the font/display problem.  Worth a try though!

Adam

---

### Post by apease on 2008-02-23
More follow-up experiments - 

- often when booting up the system will fail to recognize the external monitor.  Going to
Administration->Screens and Graphics and clicking Model then Detect enabled the system to switch over to the external monitor.  However, when I rebooted, the system forces 800x600 resolution.

- I hit F2 on bootup and on the BIOS screen I went to Display, and changed the screen from [Auto] to [LCD + analog] (not quite the exact text), then continued to boot.  Now I get both laptop and external monitor, but the resolution is limited to 1400x1050 instead of the full 1680x1060 that the monitor is capable of.

Still no good solution.  I hope Ubuntu 8 has better laptop display driver support.

---

