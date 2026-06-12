---
title: "usb install failed(?), but installed wubi?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by maraym on 2011-10-18
Hi - 

I created a bootable USB stick (via Universal USB Installer, as specified in [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) and **successfully booted** into Ubuntu 11.10.

Then I **tried to install** from the same USB stick, both via the boot menu, as well as via the install option on the Ubuntu desktop.  

In both cases, the install process 


[LIST]
[*]exited the Ubuntu desktop (after the "install inside windows XP screen),
[*] told me to remove the install media and press enter
[*]rebooted into Windows
[/LIST]
 
Now, upon logging in to Windows, I see that Wubi has been installed into the "Startup" menu under "All Users".  

Is this the expected behavior when installing "inside Windows XP", or did the install in fact fail?

**Should I proceed with the prompted Wubi install?**

If so, did I waste several hours (and 700MB of Ubuntu's bandwidth) downloading the .iso, the Universal Installer, etc??


If it makes any difference, it's a Sandisk Cruzer 8GB drive.  It doesn't seem to have the U3 Launchpad.  I'm attempting to install onto a 3 year old Asus eee 900HA

Thanks

---

### Post by bcbc on 2011-10-18
The ubuntu installer (ubiquity) will offer a wub install (install inside windows) if you have no available partitions. In other words you have the maximum 4 primary partitions. That's the only way to install Ubuntu unless you can delete one of these partitions.

So if you say "yeah" it writes wubi.exe into the Startup programs under your windows install.

Point 0: if you want a direct install, delete a partition - do some backup/data juggling etc. Don't let Windows create dynamic disks (it looks like this is a workaround to create a 5th partition but it's not supported by linux)

On Wubi:
Point 1: if you remove the USB, and let wubi run, it will download a preinstalled image (500MB). This is new for Ubuntu 11.10 and I feel that this is not the best option. [Read here about it.]("http://ubuntu-with-wubi.blogspot.com/2011/10/oneric-ocelot-1110-released.html")

Point 2: if you leave the USB in, wubi will detect it, use it and FAIL. Unfortunately wubi does not support usb installs if the usb partition is > 900,000 kilobytes. 

Point 3: if you have that downloaded ISO that you used to create the USB on your computer still you can use it to install without downloading anything again. Place it in the same folder as wubi.exe and it will use it. (Make sure the USB isn't attached).

Hopefully that makes things clearer - if not - feel free to ask any questions.

PS that wubi.exe in your startup should be setup to delete itself automatically after it runs (once you restart).

---

### Post by maraym on 2011-10-18
Thanks bcbc!

I get the logic flow of autoinstalling/autostarting wubi in Windows after detecting the error condition.  It was confusing though.  I actually moved the wubi executable out of the Startup menu and went through the process again to confirm that that was how it got there.

A message indicating that this was going to happen along with the "remove media and press enter" message would be helpful.

re: point 2 - I came across this nugget before, but thought it was a typo, as I don't understand how you could install from a 900KB USB partition, given a 700MB .iso, or 2.5MB wubi executable.  

Does this mean that I cannot install from my USB flash drive?  In which case, given the lack of CD/DVD drive on the netbook (or an available external drive), I seem to have no alternative other than wubi?

re: point 3 - good to know if I need to go that route!  Does the presence of the full 700MB .iso ameliorate the concerns you express in point 1?

Thanks again

---

### Post by bcbc on 2011-10-18
My bad, I meant 900,000 KB :) And this only affects Wubi installs, not normal installs from a booted USB

Yes if you place the ISO with wubi.exe in the same directory it will use it and not download the preinstalled image.

---

### Post by maraym on 2011-10-18
Ok, I'm going to try to repartition and do a normal install.

If I run into problems, I'll go to wubi with the .iso in the same directory.


Thanks again bcbc

---

