---
title: "Change Keyboard Layout on Server Permanently"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by Badmaster on 2011-06-29
Hi all

whenever I reboot my server they keyboard layout is reset to US layout.

I tried editing /etc/default/keyboard but to no avail...

dpkg-reconfigure console-data will correct the layout, but only until I restart.

This is on Ubuntu Server 11.04 with home dirs encrypted.

already tried this:
[http://ubuntuforums.org/showthread.php?t=1758915](http://ubuntuforums.org/showthread.php?t=1758915)

thanks in advance

---

### Post by Bachstelze on 2011-06-29
Try dpkg-reconfigure console-setup.

---

### Post by Badmaster on 2011-06-29
> **Bachstelze said:**
> Try dpkg-reconfigure console-setup.

already tried... same thing...

actually I just solved it, thanks to your comment.

I had put an invalid string in /etc/default/keyboard
dpkg-reconfigure console-setup creates a new initramfs and there it notified me that it couldn't find the defined symbolds from /etc/default/keyboard

so I looked at the dir /usr/share/X11/xkb/symbols/ and there I saw the correct layout.
then ran dpkg-reconfigure console-setup
and it works now :-)

---

### Post by MikB on 2011-08-06
I am having the same problem with Ubuntu Server.

But I'm a bit of a noob.

Could you please explain your solution in some more basic steps?

Many thanks

---

### Post by manuelsal on 2012-01-23
> **MikB said:**
> I am having the same problem with Ubuntu Server.

But I'm a bit of a noob.

Could you please explain your solution in some more basic steps?

Many thanks

I have the same issue.
Any help?

---

### Post by mrtorrent on 2012-01-24
> **manuelsal said:**
> I have the same issue.
Any help?

I'm on 11.10 Oneiric, and you have to run ```
sudo dpkg-reconfigure keyboard-configuration
``` to reconfigure the console keyboard layout

---

### Post by manuelsal on 2012-01-24
> **mrtorrent said:**
> I'm on 11.10 Oneiric, and you have to run ```
sudo dpkg-reconfigure keyboard-configuration
``` to reconfigure the console keyboard layout

Thanks, it works, but if i reboot the system i lose my config.
Any suggestion for this issue?

Thanks ;)

---

### Post by roomey on 2013-02-20
> **manuelsal said:**
> Thanks, it works, but if i reboot the system i lose my config.
Any suggestion for this issue?

Thanks ;)

Run

```
sudo dpkg-reconfigure keyboard-configuration 
```

first, then run:

```
sudo dpkg-reconfigure console-setup
```

---

### Post by oldos2er on 2013-02-20
Old thread closed.

---

