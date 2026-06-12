---
title: "Fatal Error with Edgy LiveCD during boot"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by MidKnight on 2007-03-07
First, pardon me if this is missplaced.

I recently received a newly burned Ubuntu 6.10 LiveCD from a classmate and I tried to boot to it.
Everything was fine up until after I chose my boot option. After some time with the Ubuntu loading screen, my monitor went blue and gave me this friendly message:

"Failed to start the Xserver (your graphical interface). It is likely that it is not set up correctly.
Would you like to view the Xserver autput to diagnose the problem?"

After selecting Ok, I get:

XWindow System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
              (something about [http://wiki.x.org](http://wiki.x.org) that I didn't care to write down)
Module loader present
(==) log file:"/var/log/Xorg.0.log", Time Web Mar 7
              00:31:48: 2007
(==) using config file: "/ect/X11/xorg.conf
Fatal server error:
No screens found                      f ''

After selecting Ok(?), I get even more information. I only bothered with the last couple of line though...

Primary Device is: PCI 01:00:0
ATI canidate "Device" section "ATI Technologies, Inc."
RV370 5B62 [Radeon X600 (PCIE)]
(WW) ATI : PCI Mach64 in slot 1:0:0 could not be detected
(WW) ATI : PCI Mach64 in slot 1:0:1 could not be detected
fatal server error
no screens found


After this, all I get is a black screen with a single text cursor in the upper-left.

...little help here?

---

### Post by chewearn on 2007-03-08
Try this:
Press CTRL+ALT+F1, which should gives you a text login prompt.  Use your user's name and password.  Then, at the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by MidKnight on 2007-03-08
Thanks, but I was able to find help from a friendly Ubuntu user who happened to live in the same dormitory. I'm all set now (well, I got another small problem...but thats for a different thread)

---

