---
title: "Installed Ubuntu 14.04 and laptop either crashed or keyboard/mouse not responding"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by earl-ku on 2014-04-19
This is an old trusty laptop(HP COmpaq Presario V3000) i tried refreshing with a copy of the latest Ubuntu 14.04
It was running on WinXP prior to this and was working fine albeit the occasional blue screen - very likely due to overheating(this model is known to have fan failures)
It still ran the browser and played media files all fine on WinXP

Went ahead and installed Ubuntu using the iso image, after installing, boot up was fast but once i am in the GUI, the mouse will only work for no more than 5 secs, after swirling it around - it just freezes and nothing works there after. Not sure if the laptop froze or the keyboard/mouse not working. Not sure how to determine this. 

Went ahead and reboot via Ubuntu and used the try option, it just never loads past the message that says my network connectivity is off.

Any one knows whats going on here? Laptop overheat and froze or the drivers issue with keyboard and mouse?

---

### Post by NoBugs! on 2014-04-19
How much memory does it have, if it came with Windows XP? Assuming it's not an Ubuntu bug, it's probably running out of memory and freezing. A lighter environment like XFCE may work better.

---

### Post by casawyer on 2014-04-19
Which OS 14.04 did you install?  64 bit or 32 bit?  You should of used the 32 bit.  I put it on mine laptop and had no problems other then with the Chrome that is in the program manager, didn't want to play flashplayer spots on web sites.  I ended up uninstalling the chrome they offer, and downloading the Google stable Chrome for Linux using the terminal.  It works great. 

I originally was running windows 7 and kept getting the blue screen of death, It wasn't occasional like yours.  I originally installed 10.04 LTS 32 bit and upgraded from there.   If you have the ability to download, download the earlier version 13.10 32 bit and update and upgrade from there.  I hven't had really any problems other then when I was trying the beta when it was released.  




> **earl-ku said:**
> This is an old trusty laptop(HP COmpaq Presario V3000) i tried refreshing with a copy of the latest Ubuntu 14.04
It was running on WinXP prior to this and was working fine albeit the occasional blue screen - very likely due to overheating(this model is known to have fan failures)
It still ran the browser and played media files all fine on WinXP

Went ahead and installed Ubuntu using the iso image, after installing, boot up was fast but once i am in the GUI, the mouse will only work for no more than 5 secs, after swirling it around - it just freezes and nothing works there after. Not sure if the laptop froze or the keyboard/mouse not working. Not sure how to determine this. 

Went ahead and reboot via Ubuntu and used the try option, it just never loads past the message that says my network connectivity is off.

Any one knows whats going on here? Laptop overheat and froze or the drivers issue with keyboard and mouse?

---

### Post by earl-ku on 2014-04-20
> **NoBugs! said:**
> How much memory does it have, if it came with Windows XP? Assuming it's not an Ubuntu bug, it's probably running out of memory and freezing. A lighter environment like XFCE may work better.
Its on 1GB RAM ... will check out XFCE

> **casawyer said:**
> Which OS 14.04 did you install?  64 bit or 32 bit?  You should of used the 32 bit.  I put it on mine laptop and had no problems other then with the Chrome that is in the program manager, didn't want to play flashplayer spots on web sites.  I ended up uninstalling the chrome they offer, and downloading the Google stable Chrome for Linux using the terminal.  It works great. 

I originally was running windows 7 and kept getting the blue screen of death, It wasn't occasional like yours.  I originally installed 10.04 LTS 32 bit and upgraded from there.   If you have the ability to download, download the earlier version 13.10 32 bit and update and upgrade from there.  I hven't had really any problems other then when I was trying the beta when it was released.
yeah forgot to mention that, its 32bit version ... 
ok will go check out some mirrors and try that backdated version ...

am contemplating of trying to reinstall  it once ...

***update - went ahead and reinstalled only option i changed this time is the LVM, and this time after the initial restart, i can still get to use the cursor, but nothing is responding after clicking on everything on desktop ... weird

---

### Post by tgalati4 on 2014-04-20
Try booting into Rescue Shell from GRUB.  If the computer boots to a terminal screen, then perhaps your laptop has a graphics card issue.  It's not uncommon for graphics chips to delaminate when they get hot can cause the system to freeze.  If it had hardware issues with XP, then chances are those hardware issues still exist.

---

### Post by earl-ku on 2014-04-27
Mnage to install 13-10 version and got a minot hickup with the wifi driver ... but finally got it working. 

this was posted from the old presario machine ... a lil slow but its working ... the laptop is now revived... thanks guys for the suggestions and all

---

