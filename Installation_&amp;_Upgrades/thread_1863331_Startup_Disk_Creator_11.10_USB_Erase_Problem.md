---
title: "Startup Disk Creator 11.10 USB Erase Problem"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by ProntoAnthony on 2011-10-17
I'm trying to download a copy of 11.10 to a usb drive. It is 2.0 MB and presently has a 10.04 image on it. The error is 

org.freedesktop.DBus.Python.dbus.exceptions.DBusException: com.ubuntu.USBCreator.Error.NotAuthorized

When I click the Help button I receive another error:

The URI 'ghelp.usb-creator' does not point to a valid page.

Any help would be appreciated.

---

### Post by gordintoronto on 2011-10-17
Full Circle Magazine issue 45, page 13 tells you how to use Multisystem. It's not perfect, but it made a flash drive which I used to install 11.10.

(After creating the drive, it crashed.)

---

### Post by ProntoAnthony on 2011-10-17
Thanks, but no help there. It asks me to connect a FAT32 formatted volume to begin. I can't format or erase the USB drive, so I'm still stuck.

I used gparted to format the usb as FAT32, yet the program still doesn't see the usb drive mounted.

wish I knew the mount command. "mount /dev/sdc1" doesn't work.

---

### Post by _sleeper on 2011-10-19
I have a similar problem. It seems that usb creator cannot erase my usb stick. It tries to do it, but for some reason it keeps looping endlessly and creating identical clones of my usb stick.

---

### Post by Unclown on 2011-12-30
Problem: Trying to install to a 2GB USB memory stick, using startup disk creator - select my dvd to install from (I booted from it), choose to erase disk, hit Yes, then multiple (almost identical) memory sticks pop up next to (within the usb-creator-app) the original one, and a memory stick file-browser window pops up, and usb creator sits there spinning its wheels doing nothing.


Open a terminal window.

Type 'usb-creator-kde' - the startup disk creator runs and we are back to square one.

Type 'usb-creator-gtk' - the startup disk creator runs (looks a little different, but not much) - AHA!!

This one says "The device is not large enough to hold this image" - my DVD ISO (the image/OS I am trying to install is too large to fit on my memory stick - I need a larger memory stick or a smaller ISO image) - now why is this so hard...


HTH someone.

---

### Post by Unclown on 2011-12-30
Visual info - terminal window with commands, file browser window, usb-creator-xxx window.


HTH.

---

### Post by ProntoAnthony on 2011-12-31
I just reinstalled the usb-creator-kde and then was able to erase my usb stick, copy the iso image, and boot from the stick without problems. Yippie!

---

