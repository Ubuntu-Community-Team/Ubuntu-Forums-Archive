---
title: "Adobe plugins for Firefox"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by gamphd on 2009-12-26
I don't know if the problem is with Adobe, Firefox, or Ubuntu, but regardless of whether I try to download Reader or Flash directly from the Adobe site or from the Firefox Plugins menu, Adobe hands be a .bin file for Reader or a lib*.so file for Flash and expects me to do everything manually to get Ubuntu to recognize it and know how to run it (the .bin file) or where to put it (/lib, /lib64, /usr/lib, /usr/lib64, or some subdirectory thereof).  Isn't this supposed to be automated?  If not for me, a relatively experienced Linux user of 7 years and UNIX user of 25, then for beginners at least?

I'll figure this out eventually, just as I finally figured out, after several reboots into Vista, that setting the WEP key type to shared was the way to get the network manager to stop spinning its wheels and connect me to the wireless LAN.

---

### Post by taurus on 2009-12-26
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
should take care most (if not all) of the plugins for you.

---

### Post by gamphd on 2009-12-26
Well, that almost worked, but instead of completing, it starts installing Java and then uses ANSI escape sequences to display a Sun terms and conditions document with no way to exit it other than by closing the window, which leaves an orphaned process running.  I still get the prompt to upgrade Flash, because it apparently never got that far.

Norton Partition Magic also claims to support Linux, but it will move a Linux partition without correcting the boot block for the offset.

---

### Post by taurus on 2009-12-27
Use the Tab key to highlight the <OK> at the bottom to accept Java license.

---

### Post by gamphd on 2009-12-27
At any rate, Firefox itself sometimes brings up a prompt that a Flash plugin is needed, and if I click that button, it installs it correctly, despite Adobe.  But it doesn't do that for PDF.  It just asks what to do with the file.  I finally realized that if I chmod'ed the .bin file and ran it, I would get an installation.  But even after running the Browser script manually and overwriting what was already installed, it still asked what to do with PDF files, so I picked Adobe Reader and said to pick that automatically in the future.  The annoying thing is that I still have to clear the downloads every time I get a PDF file.

---

