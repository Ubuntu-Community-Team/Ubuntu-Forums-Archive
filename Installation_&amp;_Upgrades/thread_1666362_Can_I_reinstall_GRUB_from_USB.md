---
title: "Can I reinstall GRUB from USB?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by JacobVengeance on 2011-01-13
Well I was trying to get BURG to work, but for some reason it just goes to a command line, so is there a way I can reinstall GRUB using a USB drive? I need to prepare it on Windows.

---

### Post by presence1960 on 2011-01-13
> **JacobVengeance said:**
> Well I was trying to get BURG to work, but for some reason it just goes to a command line, so is there a way I can reinstall GRUB using a USB drive? I need to prepare it on Windows.

use your Ubuntu Live CD/USB to reinstall GRUB.

What version of GRUB do you have? What version of Ubuntu?

If you don't know then we need more info, do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by C.S.Cameron on 2011-01-13
Install grub2 from Live CD:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This also works booting a Live USB made using Startup Disk Creator or UNetbootin.

---

