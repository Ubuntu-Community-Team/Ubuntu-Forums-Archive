---
title: "Installation to HDD from USB fails with blank screen"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by kmir on 2012-05-28
I have a somewhat similar problem: I am trying to install Ubuntu 12.04 from a USB stick. Creating the USB stick and booting from it have been successful. I go through the installation, and at the end it says, "everything worked, thanks very much, please restart."

So I do that (from the HD), and get a black screen with a cursor blinking. When I insert the USB stick, still the same thing. When I exclude the HD from the boot sequence, Ubuntu starts, and it says it has booted from the HD. I can delete the files on the USB stick. 
But it still won't boot just from the HD.

---

### Post by drs305 on 2012-05-28
Post moved to its own thread.

You might have a video driver problem. With the USB stick removed, boot to the GRUB prompt. Hold down the SHIFT key until the menu appears if it doesn't appear otherwise.

Press 'e' to edit the menu. Cursor to the end of the 'linux' line and remove everything after *ro* and add *nomodeset*

Press F10 to boot. If you get to the Desktop, try installing your video card's driver via Additional Drivers.

Another way to try is to boot the Recovery mode from the menu and select the option for failsafe video, if it's an option.

---

