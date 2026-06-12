---
title: "Lubuntu - System Problem Detected!"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by jp734 on 2014-01-14
After updating the system (lubuntu 13.10 64bit), I've been getting the error "System Problem Detected!" and could not figure this out.  I tried to make sure everything is up to date **(sudo apt-get update)** and everything is up to date.

I tried removing the driver for my ATI card and deleted the xorg.conf file to see if it will boot using the vesa driver, still the same result.

It updated the kernel from **3.11.0.12.generic** to **3.11.0.15.generic** but on boot advance option, I can select "...0.12.generic" and that didn't work neither.

What can I do to resolve this?

---

### Post by TheFu on 2014-01-15
a) sudo apt-get update - doesn't actually update the system, it just updates the list of package AVAILABLE.  To update the system, use 
**sudo apt-get upgrade** to stay on the same kernel version or **sudo apt-get dist-upgrade** to allow newer versions of software and kernels to be installed. Don't worry - it will NOT update to any new release.

b) To figure out any problems, look at the system log files. Without that, we are pissing in the wind.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) explains.

---

