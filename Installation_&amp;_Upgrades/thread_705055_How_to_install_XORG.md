---
title: "How to install XORG?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by drywood on 2008-02-23
I was trying to configure the ATI Radeon Mobility M6 of the flybook in the still installed UBUNTU 7.10 (first steps with linux!), but i couldn't. Looking for help in internet I ALWAYS met Xorg.

What is this?
Should I install it?

I tried to download it, but I haven't only a file. When I was looking for xorg download link I found myself in a jungle of files!

Where can I download a simple xorg installation file?

Thank you.

---

### Post by em3raldxiii on 2008-02-23
If you have Ubuntu installed, you already have xorg installed as xorg is the implementation of the X Window system.  You don't typically need to know much about it, other than you sometimes have to edit the configuration file located here:

/etc/X11/xorg.conf

This file contains a number of important configuration settings, including which drivers and modules to use for specific pieces of hardware.

To edit it, there are a number of applications you can use.  I usually use gedit because I like graphical editors.  Many people will recommend using a program called vi or a program called nano.  Those are command-line editors and are great if you don't have access to a graphical desktop (like if you accidentally broke your xorg.conf file and your system won't boot with the graphical interface).  You have to use super-user to edit the file, hence:

```
gksu gedit /etc/X11/xorg.conf
```

Note that if you are using a command-line editor such as vi or nano, then you would type this:

```
sudo nano /etc/X11/xorg.conf
```

In your case, since it sounds like you are trying to get your ATI video card to work with proprietary drivers, you will likely have to edit a small portion of this file.  If you are very unfamiliar with doing this, the first thing you should always do is back up the file:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[date]

```Then if you boot your system and it does not boot properly (leaving you with a black screen after a bunch of errors), you can replace the xorg.conf file with the backed up one with this command:

```

sudo cp /etc/X11/xorg.conf.backup[date] /etc/X11/xorg.conf

```It's important to note that the X in X11 is a CAPITAL X, not lower case.

Hope that gets you back on track :D

---

### Post by drywood on 2008-02-23
Thank you very much em3raldxiii.
The puzzle started.

---

