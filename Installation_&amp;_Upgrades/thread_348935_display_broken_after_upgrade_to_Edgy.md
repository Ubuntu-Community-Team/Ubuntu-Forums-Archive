---
title: "display broken after upgrade to Edgy"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by sqlplus on 2007-01-29
I had a working 6.06 kubuntu system.

Then, I tried to upgrade to Edgy. At first things seemed to work. Then, after (think) updating some more packages, I'm left with not being able to boot into the regular x display.

When i boot up I see the progress bar for about 30 seconds, then a black screen. When I hit enter I see a login prompt, but also, a bunch of error messages scrolling by (messing up the login prompt) that read:

hdc: error code 0x70 sense_key: 0x02 asc: 0x30 ascq: 0x00

I think that this error message was something that was always happening even when my system was working under 6.06. What is it and what does it mean?

I assume that my x.org config must be broken. Would that be right? How do I troubleshoot and fix things? I've tried the dpkg reconfigure command but maybe I chose the wrong options because that does not seem to help.

system: hp pavillion dv8000 laptop

Thanks in advance!  :)

---

### Post by dougfractal on 2007-01-29
You could try using a live disk and copying its /etc/X11/xorg.conf file to your hard drive.

were you using nvidia/fglrx drivers if so in the xorg.conf file if so 
change the Section "Device" driver
  Driver          "nv"
or 
 Driver          "ati"
 
 sudo dpkg-reconfigure -phigh xserver-xorg        # adjusts existing xorg
 sudo dpkg-reconfigure xserver-xorg                  # rewrite

for the restricted drivers you may need to update your linux-restricted-modules

---

