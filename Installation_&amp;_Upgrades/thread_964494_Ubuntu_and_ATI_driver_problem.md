---
title: "Ubuntu and ATI driver problem"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by sr71pav on 2008-10-30
Like everyone else, I just upgrade to 8.10.  I've found that I can't even get to the login screen when I try to use the ATI drivers.  If I reset into safe mode and allow it to reset the Xorg server, it fixes tisle,f but reverts back to the linux ATI drivers, not the ATI proprietary drivers.  Any thoughts as to fixing this one?

---

### Post by martrn on 2008-10-31
This maybe the solution.  If you look at this it will explain more clearly about bulletproofx or failsafeX :
[https://wiki.ubuntu.com/BulletProofX]("https://wiki.ubuntu.com/BulletProofX").

BulletProofX Does not generate a valid X11 config file, so if you look at your **/etc/X11/xorg.conf** with BulletProofX it will not be valid under the specification required by xorg for your X11 windowing system.

You do not have a valid X11 file (or Xorg.conf) file for you windowing system that will be required by your ATI driver.

In effect BulletProofX is kicking in and forgeing a situation whereby it displays a screen of lower or unspecified resolution in order to display some sort of screen.

If in your in /etc/gdm/gdm.conf you comment out the line that reads
> FailsafeXServer=/etc/gdm/failsafeXServer
then this will disable the functionality BulletProofX.  I personally would call it bulletX becuase it puts a great big bullet through all of your troubleshooting problems and causes a situation whereby you have no valid X11 or xorg.conf file.

Hope that helps.

---

