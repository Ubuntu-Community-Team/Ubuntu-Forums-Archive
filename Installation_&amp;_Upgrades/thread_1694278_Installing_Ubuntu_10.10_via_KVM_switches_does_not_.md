---
title: "Installing Ubuntu 10.10 via KVM switches does not work"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Jean-marc Adamo on 2011-02-24
[SIZE=3][FONT=Calibri]I tried to install Ubuntu 10.10 on a PC connected to the {keyboard, video and monitor} set (the console) through a KVM switch (a Trendnet 4-ports USB KVM switch, hence not an exotic one). The installation failed. Apparently, the Ubuntu installer fails to identify the monitor through the KVM switch and starts freezing. This note reports about a few observations I’ve made and makes a few suggestions that could help fix this problem in the versions to come (at least, I hope so).[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](1) After trying to install, through the KVM, I waited for a few minutes and directly connected the PC to the console. The monitor displayed the Ubuntu logo (the name underlined with the red dots). The PC was blocked. Nothing to do except rebooting.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](2) I next tried to install with the PC directly connected to the console. The installer succeeded this time. After logging in, I checked the monitor features (System->Preferences). They were right: the monitor was correctly identified (right name displayed) with the right resolution.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](3) I reconnected the PC through the KWM switch. I checked the monitor features as above. The monitor was no longer correctly identified (declared as unknown) with proposed resolution options  far below the real monitor capabilities.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](4) I rebooted the PC (still connected through the KWM switch): black screen. I directly reconnected the console to the PC. The screen was displaying the Ubuntu logo as in (1). The PC was blocked. Nothing to do except rebooting (with a direct connection between the monitor and the PC, of course).[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]This PC has a multiple boot with two other MS operating systems: XP and Vista. I had absolutely no problem with installing and next tuning the screen parameters using the appropriate monitor manager accessed via the MS Control Panel. There, the default screen resolution can appropriately be set so that the screen can be used with the right resolution (both after logging in and at booting time).[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Solving the above mentioned Ubuntu problems seems to be straightforward.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](a) Isn’t it possible to make the Ubuntu installer ask for the monitor features or work in degraded graphical mode in case it fails identifying the monitor? This would allow it to carry on its job and succeed.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri](b) The monitor manager accessed via System->Preferences should be extended so that it could allow setting default values for the monitor parameters that should be used both after logging in and at booting time (the current monitor manager provided with Ubuntu actually is useless) .[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thank you.[/FONT][/SIZE]
[FONT=Calibri]Jean-Marc Adamo[/FONT]

---

