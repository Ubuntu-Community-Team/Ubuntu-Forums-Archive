---
title: "xorg-driver-fglrx causes jaunty to crash, help please"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by fborcic on 2010-02-20
Hello,
i was recently trying to run some opengl apps on ubuntu, and installed new drivers for intel. The problem is that now, every time it reaches login screen it crashes. I'd like to remove it, but i can't. Recovery console asks for root password. Is there a way to do it from a livecd?
                                              Fran

---

### Post by quadproc on 2010-02-22
I do not know any of the details of your situation but having had a lot of trouble myself with video card drivers I can suggest a thing that _may_ get you running again.

Get the system running in recovery mode (or use some other means to obtain edit access for the /etc/X11/xorg.conf file; I booted from an old but running version of Ubuntu and mounted the problematic file system temporarily so that I could use gedit to work on the file) and change the driver from fglrx to ati (or to vesa if you can stand a really primitive but robust driver).  Then start the X server, or reboot.

Note: I had a lot of trouble with Ubuntu 8.10 not starting the X server and just leaving me with a glass teletype interface.  I found that the problem was the X server; it was version 1.5 and it could not tolerate two video systmes in the machine (in my case, two ATI cards of the same type rigged for crossfire operation but others have had trouble when one video system is on the motherboard and another is a plugin card).  The X server sees two cards and cannot figure out which one is the primary card so it just gives up and quits executing, without even creating a log file.  I worked around this by adding a busid specification to my xorg.conf file:```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:02:00:00"
EndSection

```
This allowed the X server to choose one card as a primary device and it worked OK thereafter.  Ubuntu, in versions above 8.10, is using version 1.6 of the X server and this version might not have the conflict problem so this workaround may not be necessary any more; I haven't checked.

Another note: many people have learned that ATI is not supporting their older video cards with fglrx.  You may need to check your card's model to see if it is supported.  If not, then using the "ati" driver (rather than "fglrx") may be an option.

I may have misunderstand your circumstances so perhaps none of this applies, but good luck!

Quadproc

---

