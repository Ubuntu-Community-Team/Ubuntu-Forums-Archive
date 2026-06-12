---
title: "dual boot best practice"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by dkruitz on 2010-01-22
I've got a PC I've reloaded with XP Pro that I need for work at times, but I've used Ubuntu and want to make it my primary OS.  So I tried the wubi.exe windows installer and installed ubuntu on an NTFS U: drive.  I was surprised how it shows up in windows and wondered if this is some oddball file system, and are there any risks in having a dual boot using this version (on an NTFS partition), or should I boot off the CD and let it take empty space for more traditional linux partitions as needed?  (I'm on a single 250GB sata drive, but am planing to add a 2nd IDE drive later - will this cause any issues re: /hda /sda ?)

Thanks for looking!
Dan

---

### Post by steveneddy on 2010-01-22
Why don't you simply run Ubuntu in a virtual machine like VirtualBox?

Seems easier to me than partitioning.

---

### Post by kansasnoob on 2010-01-22
My only real complaint with Wubi is explained here:

[http://wubi-installer.org/faq.php#requirements](http://wubi-installer.org/faq.php#requirements)

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover **Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem**, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


And power outages are very common where I live!

I prefer a true dual boot something like this:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

NOTE: The steps regarding grub in that tutorial do not apply to 9.10 (Karmic) and later as it now uses grub2!

---

### Post by dkruitz on 2010-01-22
It's already dual booting - just asking if having Ubuntu on an NTFS partition is a best practice, or is it better to boot off the Live CD and install it all linux partitions. 

If I run virtual box, the virtualized system would be slower wouldn't it?   Or is the performance pretty good running an XP pro VM inside Ubuntu?

---

### Post by garvinrick4 on 2010-01-22
Here is a site with a graphical install to help you out.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

