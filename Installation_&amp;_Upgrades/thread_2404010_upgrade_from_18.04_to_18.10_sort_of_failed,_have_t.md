---
title: "upgrade from 18.04 to 18.10 sort of failed, have to manually startx"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2018-10-18
Simple I did the upgrade just now.
I rebooted, and it only shows text on the screen, part of the booting process.
I goto a console terminal window, login user and password.
Then I type startx, and I get the desktop.
The desktop is missing all my gnome extensions on the top.
When I plug in a usb drive, it does not mount in the file manager window, but it is present in gparted.

**So how do I get it to start gnome automatically?**
[B]And I have no sound anymore, just says 'dummy output'
[/B]
And what about usb drives auto mounting? (Ok, when I closed gparted, it appeared)

The menus are all gone like places and apps on the top bar, only shows activities. (ok, I got the extensions upgraded and they are working again)

---

### Post by sdowney717 on 2018-10-19
I had to do a fresh install, I was getting too many errors.
Then I wiped that install as I was getting grub rescue and did not know why then, so I left it overnight to think why. 

Somehow when it was booting I was hitting functions keys to get into menus to boot the usb to install, and I must have accidently loaded bios defaults.
I have 3 hard drives, so even though I installed it properly, the PC bios was not booting from the correct drive, hence 'grub rescue' prompt.

Now everything is working, of course I have to download and reinstall everything.
This is second time where doing the   upgrade the os it fails.

---

