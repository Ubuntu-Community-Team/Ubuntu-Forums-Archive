---
title: "Hardy ATI Radeon HD2400Pro problems"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by RVCollins on 2008-06-08
I'm new to Ubuntu.  Installed Hardy from a download (clean start) and the first phase went fine using the on MoBo Generic VGA.  Reinstalled the Radeon HD2400 card and could not get past the splash screen.  Reading all the other post (thank you all) I discovered alt+F1 and EnvyNG which installed the ATI (8.47.3) driver and Catalyst Control Center.

My maximum resolution selectable is limited to 1024x768 and not the desired 1920x1080 supported by the card and monitor. Also the I've lost the sound which previously was working fine.

I suspect that I need to disable/delete the previously used on MoBo Generic VGA and the ATI RV610 audio drivers that EnvyNG installed but I've found no way to do this.

Thanks in advance for your suggestions.

Bob

---

### Post by jashin on 2008-06-08
This tutorial ([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")) solved my problem with ATI Radeon HD2600. Try Method 1 - I was unable to get my ATI running with Catalyst driver. You can list all aticonfig parameters if you execute [FONT="Courier New"]aticonfig --help[/FONT]
Good luck! :-)

---

