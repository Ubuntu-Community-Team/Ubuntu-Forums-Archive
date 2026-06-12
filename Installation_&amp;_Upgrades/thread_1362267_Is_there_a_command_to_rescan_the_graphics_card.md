---
title: "Is there a command to rescan the graphics card?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by carl99fan on 2009-12-22
I am having problems, sudo dpkg-reconfigure xserver-xorg is not helping me @ this time... I have thought about using a live cd to help me but I don't know what to do.

Please how do I start over with my Graphics!?

---

### Post by mikewhatever on 2009-12-22
Can you tell us what graphics cad it is and what's the problem. What do you get after running <dpkg-reconfigure -phigh xserver-xorg>?

---

### Post by carl99fan on 2009-12-23
> **mikewhatever said:**
> Can you tell us what graphics cad it is and what's the problem. What do you get after running <dpkg-reconfigure phigh xserver-xorg>?

Package `phigh' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: phigh is not installed

I have an intel 950 something or other if I remember correctly. 2 gen on board.

---

### Post by carl99fan on 2009-12-23
This hard drive was @ one time in another machine, that used nvidia on board graphics. I have moved it to a different machine, and I have been trying a lot of different things trying to get ubuntu to autodetect it. no luck so far.

---

### Post by mikewhatever on 2009-12-23
Fixed the command above, sorry about that.
So the problem is that the new machine can not detect the hard drive? Do you have problems booting or is there a no GUI problem only? If you can get to command line, it might be possible do remove the nvidia related packages, which may in turn make reconfiguring xserver more successful.

---

### Post by adam814 on 2009-12-23
Please post the output from this command:

grep Driver /etc/X11/xorg.conf

This will show whether your system is using the proper video driver for your system (or instead loading the old nvidia driver or the generic vesa driver)

If it is using the proper driver you can adjust resolution and color depth under System > Preferences > Display.

---

### Post by carl99fan on 2009-12-23
grep Driver /etc/X11/xorg.conf
Gave me Driver "nvidia"

---

### Post by adam814 on 2009-12-23
Try this:
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
That way you can get your old xorg.conf back if you need it.

If you start X without the xorg.conf file it should try to detect which driver you need.  You might get a low-resolution screen, but you can adjust this once you're logged in to your desktop environment.

---

### Post by carl99fan on 2009-12-23
> **adam814 said:**
> Try this:

That way you can get your old xorg.conf back if you need it.

If you start X without the xorg.conf file it should try to detect which driver you need.  You might get a low-resolution screen, but you can adjust this once you're logged in to your desktop environment.

Awesome. I am back in the game. Thank you very much.

---

