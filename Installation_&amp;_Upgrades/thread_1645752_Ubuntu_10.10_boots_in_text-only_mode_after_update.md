---
title: "Ubuntu 10.10 boots in text-only mode after update"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by bobhurt on 2010-12-15
I originally installed Ubuntu 9.10 on my old 32bit Pentium Hp/Compaq dc7100 business desktop, which also has Windows XP installed.  It worked fine with the gnome interface, showing the desktop on boot.  Over the past year, I used the built in update manager to update the system and apps to 10.04, then 10.10, and a couple of days ago to further 10.10 updates.

Last time I booted, it performed a disk check, then booted to a text-mode login-prompt, like on the old UNIX systems before the X gui system got developed.

I have no clue how to launch gnome or x11 and get my desktop back. I don't have the knowledge (or patience) to operate Linux from a command prompt in text-only mode.

Will someone tell me how to get UBUNTU 10.10 to launch x11 gnome and show my desktop?

I remember having the same problem when I first updated to 10.10, but I don't recall what I did to get the desktop to appear on the display.

---

### Post by sikander3786 on 2010-12-15
From the command line, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, it is case sensitive. Make sure you type it correctly. It might throw an error like file not found, ignore and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo shutdown -r now
```

If that still boots to the terminal, post the output of this command.

```
lspci | grep VGA
```

---

### Post by bobhurt on 2010-12-18
I looked in /etc/X11 and found no xorg.conf, but did find xorg.conf.failsafe.

When I restarted, the system still came up in text mode asking me to log in, which I did.

lspci|grep gave this result:

VGA compatible controller Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)


I'd really like to know how to troubleshoot this myself.  To do that, I need a description of the boot sequence.  Doesn't some kind of RC file exist somewhere that lists all the startup commands, including the launch of X11 and Gnome?

Also, why do users have to face this nonsense of screwy booting after update?  When the system automatically encourages the user to update to a new version, it should set up the boot with the proper commands and drivers that it used BEFORE, in the earlier configuration.  Obviously, the system did not run X11 and Gnome.  I did not change the graphic card.  I installed some additional memory, but I that did not mess up the boot into GUI mode BEFORE the update to 10.10.

I have no clue where to find a list of popular commands needed to get the system going into GUI mode manually.  To me that seems strange, particularly after 20 years of Xwindows usage in UNIX-like systems.

Also, if I have this no-Gnome boot problem after update to 10.04 and 10.10, surely thousands of others have the same problem.

I seem to recall executing some command when I lost GUI after updating to 10.04.  Maybe I executed XINIT.  I just don't remember.

---

### Post by ping-wu on 2010-12-18
I have experienced a similar problem when I installed 10.10.  The problem is that the original iso does not have the correct driver for some of Intel's graphic chips.

I finally solved the problem by:

1.  Boot into safe mode (but still in graphic mode)

2.  Issue sudo apt-get update (this step is actually not necessary)

3.  Go to System -> Administration -> Update manager and Upgrade your kernel and everything else

4.  Reboot

5.  Problem solved!


> **bobhurt said:**
> I looked in /etc/X11 and found no xorg.conf, but did find xorg.conf.failsafe.

When I restarted, the system still came up in text mode asking me to log in, which I did.

lspci|grep gave this result:

VGA compatible controller Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by miross on 2011-01-22
Thanks sikander3786!   This worked perfectly for me!

---

### Post by Franco1987 on 2012-04-30
Gracias sikander3786 it works perfectly!

---

### Post by oldos2er on 2012-04-30
Old thread closed.

---

