---
title: "Installing fonts"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by bandara on 2006-10-26
I am completly new to Linux. I use Ubuntu dapper drake.I downloaded some fonts from internet but do not know how to install them.

Some files are .ttf and some are .tar.gz and one .tgz format.

I tried to drag and drop .ttf files but I do not have the permission to write to usr/share/fonts directory.

How do I install it?

Thanks.

---

### Post by coffeecat on 2006-10-26
So long as you are using Ubuntu with The Gnome desktop, the easiest way to install .ttf files is as follows:

From the top menu - System > Preferences > Font. A window opens. Click on the 'Details' button. Another window opens. In the second window click on the 'Go to font folder' button. This opens a Nautilus window that is a virtual folder of all your installed fonts. Simply drag and drop your .ttf files into it. Nothing may appear to happen, but it does! Now restart the Xserver with ctrl-alt-backspace or a reboot. Your fonts are now installed.

Actually, I think they might be available straightaway even though they don't show up in that virtual folder until after you have restarted X. Try, and if not restart X or reboot.

As far as the tar.gz files are concerned, you'll have to untar them first and see what type of fonts you've got there. Simply double-click on the tar file and follow the instructions in the window. If the files are not .ttf, post back with details.

**Edit:** By the way - you don't have to worry about permissions this way.

---

### Post by bandara on 2006-10-28
Thank you. It worked.

---

