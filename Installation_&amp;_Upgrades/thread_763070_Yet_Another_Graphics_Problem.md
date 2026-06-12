---
title: "Yet Another Graphics Problem"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by pmstirling on 2008-04-22
Hi -

I've downloaded the current ubuntu CD image (7.10) and am trying to run the live CD version (ie boot ubuntu off the CD). It boots ok but fails when X is started - it attempts to display the desktop (or whatever it is), but the grahpics are totally corrupted with vertical colored lines.

I've tried safe graphics mode and the various boot options (noacpi, irqpoll noapic, vga=771), no luck. I can get to the other consoles (Alt-Fkeys) and use the command line ok; the X server messages show no errors.

I have an old Fujitsu laptop with the Intel 830M graphics chip (the i810 linux driver).

I have used linux on this laptop before (Redhat) with no problems, and just tried an old Mepis CD I have, again no problems. Perhaps there's a new bug in the i810 driver?

Any suggestions would be welcome!
cheers
patrick

---

### Post by Pumalite on 2008-04-22
If you want to install; use the Alternate CD.

---

### Post by NoWayBill on 2008-04-22
Perhaps it's loading the wrong driver?

How to install the correct driver to a live CD boot.

This isn't necessarily a good solution if you want to run from the live CD because you'll have to do it every boot.
But if you want to install from it ......

You need to know the proper name of the video driver.

When the video fails switch to command line, **alt+ctrl+backspace**.
Your network interface should be up, if not **sudo ifup eth0** or whatever your interface is called.
Then...> sudo apt-get install *name-of-driver*

This might take a few, once it's done, shutdown X with...

**init 3**

It will start shutting down services and will seem like it hung at this step, just hit enter to get a prompt back then...

**init 5**

the X server *should* restart and load fine using the specified driver.

---

### Post by Wazoot on 2008-04-22
Yeah. check and make sure you have the right drivers. I had the same problem with the new beta Ubuntu (8.04). but i reverted back to 7.10 with no problem. :confused:

---

### Post by nobles on 2008-04-22
It appears there is some bug in the Intel drivers that affects the Xorg startup from what I've been able to find.  I have the same issue with a stock Panasonic CF-28 Toughbook and I wouldn't be surprised if every notebook with an Intel based video chipset had issues.  Both the livecd and the install suffer from the same blank or corrupted screen issue.  I can, however, successfully install Xubuntu as long as I have an external monitor hooked up to the notebook, but it still won't run on the internal notebook screen even after installing and rebooting although it continues to work on the external screen (this is not a great workaround since it makes your notebook unusable without an external screen).

I believe this has been a problem going back to last fall with previous Ubuntu based distributions - it is rather disappointing to find it is still an issue with Hardy Heron.

---

### Post by PissedApache on 2008-04-25
> **nobles said:**
> It appears there is some bug in the Intel drivers that affects the Xorg startup from what I've been able to find.  I have the same issue with a stock Panasonic CF-28 Toughbook and I wouldn't be surprised if every notebook with an Intel based video chipset had issues.  Both the livecd and the install suffer from the same blank or corrupted screen issue.  I can, however, successfully install Xubuntu as long as I have an external monitor hooked up to the notebook, but it still won't run on the internal notebook screen even after installing and rebooting although it continues to work on the external screen (this is not a great workaround since it makes your notebook unusable without an external screen).

I believe this has been a problem going back to last fall with previous Ubuntu based distributions - it is rather disappointing to find it is still an issue with Hardy Heron.

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

I have a CF-27 and had to cofigure x-server to get it working. Hope it helps :)

---

