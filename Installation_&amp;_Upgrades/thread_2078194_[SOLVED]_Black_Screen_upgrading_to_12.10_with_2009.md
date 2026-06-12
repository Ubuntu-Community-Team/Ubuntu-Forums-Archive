---
title: "[SOLVED] Black Screen upgrading to 12.10 with 2009 AMD Mobo"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by marinara on 2012-10-30
Upgrade to 12.10 brought  me to a black screen.  Holding down shift got me to the grub menu, which  allowed me to boot the newest kernel in recovery mode.  Selecting  "Enable Networking" took me to a new screen, but apparently locked up.   Control+C allowed me to log in with networking.  I removed the fglrx  drivers in 12.10, allowed me to boot with x.org drivers for my 2009 ATI  graphics (780G motherboard )


  At which point I needed the fglrx drivers to run my monitor in high resolution. 



  The good news: Easy to install legacy ATI drivers with this PPA here:
  [http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

---

