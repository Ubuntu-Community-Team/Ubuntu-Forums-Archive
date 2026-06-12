---
title: "No Signal Input on display"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by suds1056 on 2010-12-10
Have a Compaq Presario SR1915AN desktop with a NVIDIA GeForce 6150 LE it has a dual boot of Windows XP and Debian 5.0.6 which would only run in 800x600 mode.
I decided to install Ubuntu 10.10 Desktop as this is what is on another different machine, thought it would be safe.
The install wouldn't work, I  would get the purple selections screen and first time chose the normal graphic mode, 10 seconds or so in to the install the scrren goes dead and i see the "No Signal Input" display show on the screen. Rebooted and selected text mode install, this time it fully installed but on reboot it again has the screen goes dead 10 seconds after you select from the Grub screen.
Any ideas why Debian works and Ubuntu doesn't

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

It is just a crazy driver issue.

From Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting first entry, press 'e' to edit it. Navigate to words "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Hopefully, you'll see the desktop this time.

Go to System > Administration > Additional Drivers/Hardware Drivers and activate the current drivers and get rid of that problem for ever ;-)

---

