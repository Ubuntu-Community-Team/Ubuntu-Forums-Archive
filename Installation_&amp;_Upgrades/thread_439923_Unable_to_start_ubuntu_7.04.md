---
title: "Unable to start ubuntu 7.04"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Ub1476 on 2007-05-11
After I have installed Ubuntu 7.04 and the laptop restarts, Ubuntu cannot start due to some problems in the xorg.config file. I get lots of error messages about graphic/video drivers, telling they are not set up correctly(?) I haven't even touched them..:confused:  It works perfect on Ubuntu 6.10. I'm using Ati Mobility Radeon x1400. Thanks in advance:)

---

### Post by diepruis on 2007-05-11
Try this:

Boot into recovery mode, then
```

nano /etc/X11/xorg.conf

```

(or use another text editor you're comfortable with)

Go to the "Device" section, then change the Driver part to "vesa". Save the file, exit nano and then enter

```

init 2

```

Then you'll need to find a guide on how to setup fglrx, or your driver of choice and follow that.

---

### Post by Ub1476 on 2007-05-11
By setting up fglrx, do you mean installing graphic driver?

If so, is this guide allright?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by diepruis on 2007-05-11
> **Ub1476 said:**
> By setting up fglrx, do you mean installing graphic driver?

fglrx is one of the graphics drivers that work with ATi cards. There are several others, like vesa, mesa, ati and radeon. Each has different capabilities, work at different speeds and support different cards. Fglrx is the only one that supports 3D, unfortunately. It's not compatible with Ubuntu's philosophy, though, and that's why it's not included in Ubuntu by default.

> **Ub1476 said:**
> If so, is this guide allright?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That guide will tell you how to install fglrx, yes.

---

### Post by Ub1476 on 2007-05-11
Thanks for your help so far, but when i have opened xorg.conf, there are no "device" section. Actually it doesn't seem to be any section at all. Just some sort of textbox (not the terminal)..

Here's the error message:

[B]Failed to start the X server (your graphical interface): It is likely not set up correctly. Would you like to view the X server output t diagnose the problem?  Yes    No.. (I choose Yes)
[/B]
[B]X window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Curren Operating System: Linux Ubuntu 2.6.20-15generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
      Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
      to make sure you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) erropr. (NI) not implented, (??) uknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 11 21:59:26 2007
(==) Using config file: "/etc/X11/Xorg.conf"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have usable configuration.

Fatal server error:
no screens found[/B]

---

### Post by helliewm on 2007-05-11
How do i boot into REcovery MODE? I have the same problem.

---

### Post by Ub1476 on 2007-05-11
Press esc (escape) when GRUB loads.

---

### Post by Ub1476 on 2007-05-11
BUMPing my thread. Still need help!;)

...

---

### Post by diepruis on 2007-05-13
> **Ub1476 said:**
> Thanks for your help so far, but when i have opened xorg.conf, there are no "device" section. Actually it doesn't seem to be any section at all. Just some sort of textbox (not the terminal)..


From the log you posted it seems you're trying to access the wrong file. Try
```

nano /etc/X11/Xorg.conf

```

(note the capital 'X' in the last part.)

---

### Post by benson444 on 2007-05-13
If the Ubuntu machine is online and you want to install the fglrx driver, try this:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

If that doesn't work::

sudo dpkg-reconfigure xserver-xorg

and choose the fglrx video driver.

Hope it helps some.

---

### Post by helliewm on 2007-05-13
This thread worked for me. I had exactly the same problem.

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

I had Feisty installed by upgrading from Edgy.  I then turned on my laptop. Hit escape at the boot menu to get into the Console and typed in ALL the commands in the above thread. I even ended up with Beryl working!

Helen

---

