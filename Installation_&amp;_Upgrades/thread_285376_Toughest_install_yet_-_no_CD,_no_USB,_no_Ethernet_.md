---
title: "Toughest install yet - no CD, no USB, no Ethernet - although I do have wireless!"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by JHawk24821 on 2006-10-26
I have a (very) old IBM ThinkPad 760L that I would like to squeeze a little life out of.  My girlfriend wants a "play" computer running ubuntu so she can get some ubuntu experience, and this laptop fits the bill nicely.

It has a built in floppy drive, and unfortunately that's about it.  No CD, no USB, and no Ethernet.  I do have an adapter that will let me use the hard drive in my desktop computer.  I have a few ideas of how this could work:

1. Using the adapter and my desktop PC, install ubuntu to the hard drive, then swap that drive to the laptop.  Hilarity will follow I am sure.

2. Using the adapter and my desktop PC, extract the ISO to the hard drive, move the drive back to the laptop, and install that way.  This raises some questions: what file format and partition scheme should be on the hard drive prior to the ubuntu install?

I would love to see this old laptop running again, so please let me know if you have any advice to offer.

- Jesse ](*,)

[UPDATE] Forgot to mention that it currently has Windows 95 installed on it.  I can boot into Windows 95 without error, if that helps.

---

### Post by lazyart on 2006-10-26
According to [http://www.thinkwiki.org/wiki/Category:760L](http://www.thinkwiki.org/wiki/Category:760L)

ThinkPad 760L

Standard Features

    * Intel Pentium 90 CPU
    * Trident Cyber9320 video controller with 1MB
    * 10.4" TFT display with 640x480 resolution
    * 8MB memory standard
    * 810MB HDD
    * ES1688 Audio controller
    * IrDA 1.0
    * UltraBay with 1.44MB FDD
    * (2) Type II, or (1) Type III PCMCIA slot 

That's a tall order.  Maybe DSL (DamnSmallLinux) is a better distro for this?

---

### Post by arosenau on 2006-10-26
> **lazyart said:**
> According to [http://www.thinkwiki.org/wiki/Category:760L](http://www.thinkwiki.org/wiki/Category:760L)

ThinkPad 760L

Standard Features

    * Intel Pentium 90 CPU
    * Trident Cyber9320 video controller with 1MB
    * 10.4" TFT display with 640x480 resolution
    * 8MB memory standard
    * 810MB HDD
    * ES1688 Audio controller
    * IrDA 1.0
    * UltraBay with 1.44MB FDD
    * (2) Type II, or (1) Type III PCMCIA slot 

That's a tall order.  Maybe DSL (DamnSmallLinux) is a better distro for this?

I agree, although linux does run better than windows on older hardware, DSL would probably be a better choice for this laptop than Ubuntu, unless you did a very stripped down ubuntu install and no GUI.

---

### Post by JHawk24821 on 2006-10-26
Thanks for the input, and I agree.  I have looked at DSL as an alternative, but the question remains the same - how do I get it on the system?

---

### Post by Binary Jay on 2006-10-26
Can't you use a PC Card that will give you USB, and then an external CD drive to install from?

---

### Post by JHawk24821 on 2006-10-26
> Can't you use a PC Card that will give you USB, and then an external CD drive to install from?

Yes, if I had one. :)

---

### Post by hwertz on 2006-11-06
I also recommend DSL.  I haven't run anything this low-memory recently, but did with my 1st Linux systems.. 1994 or so I had an 8MB 386sx-33.  With 8MB you might be doing things in text mode, X is pretty touch-and-go.  16MB should be OK with some of those light apps DSL inclues.  32MB-64MB is a cakewalk, just as long as you don't run KDE, Gnome, or openoffice.

     As for a no CD, no USB, and no ethernet install..  just pull the disk and to the install on your desktop.  I did that with Ubuntu recently.  We got in a bunch of these weird-form-factor Compaq things (some said iPaq, even though they are not PDAs..)  No CD-ROM, no floppy, USB but they dumb things do not boot off USB.  They have great network cards and netboot support, but university politics demand we do not have our own non-IT-department-run internal network ](*,) 

     This is true of most distros.. the distro pretty much dumps all the drivers it has on the system at install, and the kernel detects what hardware you have and uses appropriate drivers at boot time.  Other than X... (graphics card support.)  X instead pre-detects your video card etc and puts that info into /etc/X11/xorg.conf.  So, with Ubuntu, I popped the hard disk in, it booted, then the screen when black for a while (I think Ubuntu restarts the X server several times to make sure it won't work), then I get a text login screen.  To fix this:

sudo Xorg -configure
(writes out xorg.conf.new with your current, graphics card information... correct except for mouse info.  xorg.conf.new looks for a mouse at /dev/mouse, which was normal for older distros.. but newer ones have the combined mouse at /dev/input/mice.. This is the combination of all mouse signals on /dev/input/mouse0, dev/input/mouse1, etc.)

sudo nano -w xorg.conf.new
control-W searched for stuff, and control-X quits (asking if you want to save your file first)... so
Control-W /dev/mouse
(replace it with /dev/input/mice)
Control-X Y

Then, to put the file in it's place
sudo cp xorg.conf.new /etc/X11/xorg.conf

restart the computer and you're good to go.

---

### Post by JHawk24821 on 2006-11-07
Thanks for the follow-up.  I was leaning towards trying what you describe, however it helps to know that someone else has already done it sucessfully.  I'll surerly give it a try!

---

