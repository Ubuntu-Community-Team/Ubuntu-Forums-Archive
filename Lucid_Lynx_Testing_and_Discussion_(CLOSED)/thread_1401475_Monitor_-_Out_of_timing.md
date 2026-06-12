---
title: "Monitor - Out of timing"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2010-02-08
With the latest Lucid kernel 2.6.32-12 I'm now getting the out of timing message when I try to boot. I've tried editing the command line (with vga=...) and it seems to make no difference. The display adapter is a nVidia 7600 GS with the nvidia-current driver (190.53) running on a Mitac-A17E monitor.
The system starts to boot and I get driver depreciated (or similar) the screen briefly goes green and then the 'Out of Timing' message is displayed. The monitor does not recover so no log-in screen is displayed.
I've even removed 'splash' from the end of the line and it makes no difference. 
The previous kernel 2.6.32-10 didn't have this problem (but I've since had to re-install due to other issues).
How should I proceed ?

---

### Post by ranch hand on 2010-02-08
Open the hood and attach a timing light to the spark plug wire number 1 and loosen the distributer.  Start computer and adjust.

Could not resist.  How does a monitor get bad timing?

---

### Post by Kevbert on 2010-02-08
> **ranch hand said:**
> Open the hood and attach a timing light to the spark plug wire number 1 and loosen the distributer.  Start computer and adjust.

Could not resist.  How does a monitor get bad timing?

I like it...
The error occurs if the display adapter tries to set the display to a vertical or horizontal frequency that the monitor can't handle. I believe it's an old problem that used to be overcome by modifying the boot parameters in grub legacy or by changing the display driver.

I may have resolved the problem. Went into safe mode with LAN cable attached to my router. Fixed damaged packages and installed 39 new updates. Then went into terminal with network support and ran
```
startx
```
Root gdm started up. Now ran System-Admin-Hardware Drivers and installed nvidia-current driver (I thought this was already running!). Now tried to reboot via the top right-hand icon menu (there was no menu at all).  Left the PC running for a few minutes and then hit the hard reset. Rebooted 10.04 OK.
Can anyone else confirm the missing log-off/restart/shutdown menu when logging in as root ? Picture attached of expected missing menu.

---

### Post by ranch hand on 2010-02-08
The button issue is strange.  It was gone for a long time on this OS (9.04>9.10>10.04) and now it and the user switcher are back.

The shut down button does nothing.  User switcher has all items grayed out.

This does bother me much as I prefer the shut down button on the lower panel and it works great.

This is the case with some of my other installs and they work on some others works.  Well user switcher is weird on all of them but the shutdown button is working on some and not others.

All on the same drive so I believe the hard ware is the same.

---

