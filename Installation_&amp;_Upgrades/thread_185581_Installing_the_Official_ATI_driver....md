---
title: "Installing the Official ATI driver..."
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by shadow07 on 2006-05-31
Ok, I have followed some of the directions laid out on the old Dapper forums.  I found the steps outlined in the [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) to no avail.  When I run fgrlxinfo, it still shows the Mesa driver.  I have attempted to compile the driver outlined in the site above, I attempted to run the ATI installer, and I cannot get the dang driver installed.

When I go through the manual steps to install the official ATI driver, module-assistant will not compile the kernel driver, as there is an issue with the makefile.

I followed the steps to the letter, and even started over from scratch (simply installing the official Ubuntu version from apt-get.)

Why the hell does this driver ALWAYS cause soooo many problems installing.

And I'm trying to install the 8.25.18 driver.


Also, when I try to remove the xorg-driver-fglrx package, I get the following:

(Reading database ... 120426 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx

---

