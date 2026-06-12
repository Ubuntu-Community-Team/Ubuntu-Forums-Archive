---
title: "Upgrade to version 10.04 LTS freez on xserver driver"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by lamachine on 2010-06-13
My Upgrade from 9.10 to 10.04 LTS freez on xserver driver.  
  Error message:
  

  Investigating xserver-xorg-core
  Package xserver-xorg-core has broken Depends on xserver-xorg
  Considering xserver-xorg 75 as a solution to xserver-xorg-core 10005
  Added xserver-xorg to the remove list  
  Fixing xserver-xorg-core via keep of xserver-xorg
 Try to Re-Instate xserver-xorg
  Investigating xserver-xorg
  Package xserver-xorg has broken Depends on xserver-xorg-input-evdev
  Considering xserver-xorg-input-evdev 75 as a solution to xserver-xorg 10005
  Added xserver-xorg-input-evdev to the remove list  
  Fixing xserver-xorg via keep of xserver-xorg-input-evdev
  Investigating xserver-xorg-video-all
  Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 1 as a solution to xserver-xorg-video-all 10005
  

  Fix:  
   My problem was xserver-xorg-video-intel
 driver from [COLOR=#000080]_[http://ppa.launchpad.net]("http://ppa.launchpad.net/")_[/COLOR].  
  

  To workaround I’ve had to ro rollback to the original Ubuntu driver.
  For this I’ve removed the  ppa.launchpad.net repos from /etc/apt/sources.list  
  

  In my case:  
  [http://ppa.launchpad.net/siretart/ppa/ubuntu/](http://ppa.launchpad.net/siretart/ppa/ubuntu/) karmic main
  [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) karmic main
  

  and install the original one again:
  sudo apt-get install xserver-xorg-video-intel

---

### Post by thdn on 2010-06-26
Same problem here, but how can i rollback xorg driver ??

---

### Post by petux7 on 2011-10-21
My update menager is in break time because it's two packages "xserver-xorg" if I will install my compiz will break completly!

---

