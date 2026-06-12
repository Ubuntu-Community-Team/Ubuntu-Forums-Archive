---
title: "What Does THIS Mean?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Mark76 on 2007-02-09
> Failed to start the X Server

X Window System version 7.0.0
Release date: November 21st 2005
X Protocol version11, Revision 0, Release 7.0
Build OS Linux 2.6.15.7, i686
Current OS Linux cpc1, etc, 2.6.12-10-386 #1 Wed February 7th 03:38:41 UTC 2007 i686
Build Date: March 16th 2006
Module Tracker: Present
Markers (--) probed, (**) from config. file, (==) default setting, (++) from Command Line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log"
(==) Using config file "/etc/x11/xorg.conf

I want answers or else I'm stuck with using a 4 gig HD forever.

---

### Post by taurus on 2007-02-09
Did you modify your /etc/X11/xorg.conf at all?  What does /var/log/Xorg.0.log say anyway?

---

### Post by az on 2007-02-09
> **Mark76 said:**
> I want answers or else I'm stuck with using a 4 gig HD forever.

What does that mean?

Did you install on one machine and then transfer your hard drive to another computer?  If that's the case, you need to boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

and then run

init 2


"Bullet-proof X" is a spec where the graphical system does not fail like this.  As it is, your graphics hardware is probed only once when you install.  If you change your video hardware, it doesn't hadle that very gracefully (for now).

---

### Post by Mark76 on 2007-02-09
It's what happened the last two times I tried to install Ubuntu on a new hard drive.  Because I don't have a CD burner I had to install Breezy Badger (from a CD I bought) first, then upgrade that to get the Upgrade Manager to show the latest release (6.06 is the one it told me about) and then use the UM to upgrade to Dapper.

When I rebooted the computer the progress status bar didn't appear and it went in to some kind of diagnostic mode, the end result of which is what you see above.

I'm currently using an old hard drive, which I upgraded to DD months ago.

---

### Post by az on 2007-02-09
> **Mark76 said:**
> 
When I rebooted the computer the progress status bar didn't appear and it went in to some kind of diagnostic mode, the end result of which is what you see above.

I'm currently using an old hard drive, which I upgraded to DD months ago.

Try booting into recovery mode (from grub) and run

apt-get -f install

and see if that does anything.

init 2 

will get you back into the GUI.

---

### Post by Mark76 on 2007-02-09
apt-get -f install told me I had two packages unupgraded.

I wonder if they're the problem?

What's the command for upgrading from grub or a terminal?

---

### Post by taurus on 2007-02-09
You mean

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Mark76 on 2007-02-09
I wish it was possible to get screen shots of boot up pages :(

---

### Post by taurus on 2007-02-09
Don't you have a digital camera or something similar to that?

---

### Post by Mark76 on 2007-02-09
Ha ha

Those things cost a bomb! :eek:

---

### Post by Mark76 on 2007-02-10
Well, I was forced to make yet another attempt at installing Dapper Drake on my new hard drive thanks to an update that claimed all the remaining space on the old one.

This time after installing Breezy (I don't have a CD burner.  Okay?) and updating that I uninstalled all Linux images before downloading the Dapper packages from the update manager.  Once I had those  the linux images came back and I'm now able to use my new HD :D

---

