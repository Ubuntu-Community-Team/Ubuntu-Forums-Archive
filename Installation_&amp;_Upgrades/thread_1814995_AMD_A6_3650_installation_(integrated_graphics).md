---
title: "AMD A6 3650 installation (integrated graphics)"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by tkordemon on 2011-07-30
I'm not sure if anyone else has had any issues getting this new processor up and running (mostly the damn integrated graphics) but I felt I would jump back on here and post this if needed

First off the easiest, and to this point, cleanest install I have had is with Ubuntu 11.04.  I had to fresh install multiple times because the restricted driver that Ubuntu tells you to install is far outdated and WILL STOP YOU FROM BOOTING INTO THE OS.  The proper drivers can be found here: 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&#10216;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Once you have this file downloaded, check out your version (semi) specific installation instructions from here:
[http://wiki.cchtml.com/index.php/Category:Installation_Documentation](http://wiki.cchtml.com/index.php/Category:Installation_Documentation)

If all goes well, as it did for me, you will need to restart before you see any magic happen.  Once you restart you should now see System->Preferences->ATI Catalyst Control Center where you will be able to adjust your settings.

NOTE: If things should happen to go wrong with the settings, heed the install instructions and remember that you can manually edit /etc/X11/xorg.conf.

Let me know if any of this is unclear or help is needed

---

