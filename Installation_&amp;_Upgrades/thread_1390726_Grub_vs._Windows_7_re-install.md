---
title: "Grub vs. Windows 7 re-install"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by rahnen on 2010-01-25
I recently had my Windows 7 crash on my dual boot Hardy 64 laptop. I used the Windows recover disk, and everything looked wonderful until I rebooted and now Grub fights Windows in an EVERLSTING reboot battle where Grub starts loading and then gets smoked by Windows and then reboots and on and on and on.

...thus I can't get into Hardy or Windows.

Is there any way to fix Grub or whatever process is fighting it???
:confused:

---

### Post by presence1960 on 2010-01-26
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ssican on 2010-01-26
Another option:

1)- How to restore the Ubuntu grub bootloader (9.04 and older)

2)- How to restore the Windows Vista or 7 bootloader

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by rahnen on 2010-01-26
Thanks for link SSICAN!

I used the GRUB 9.10 reinstall and it solved the root of the battle.

I didn't have to use the Windows boot track fix.

Thanks AGAIN!;)

---

