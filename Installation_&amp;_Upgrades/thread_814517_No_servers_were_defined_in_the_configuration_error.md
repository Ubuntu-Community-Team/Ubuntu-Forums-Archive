---
title: "No servers were defined in the configuration error during boot after editing gdm.conf"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by jabrown on 2008-05-31
In Ubuntu Hardy (with all updates installed on a VIA EPIA EN12000 fanless mythtv frontend using openchrome drivers installed by Hardy) I accidentally edited gdm.conf instead of gdm.conf-custom when setting up an automatic default timed login.

Now, instead of getting the normal ubuntu login screen, I am getting a high contrast black and white cross-hashed screen, with the following error message in a text dialog box"

"No servers were defined in the configuration file and XDMCP was disabled. This can only be a configuration error..." If I click OK the screen flickers a few times and returns to the same state.

I have tried rebooting into recovery mode, dropping into a shell, and restoring the previously working versions of gdm.conf and gdm.conf-custom, but (distressingly) the fault remained.

I've also tried:

dpkg-reconfigure gdm

... which ran without any errors, but the fault remained unchanged.

dpkg-reconfigure xserver-xorg

... which ran without error. On reboot I got an error saying that no monitor was defined. So I reinstated the previous xorg.conf, which the resulted in the original error returning. Note: while I had made changes to xorg.conf earlier in the day, the version I reinstated was working fine before the current problems started, so I don't think the problem is in xorg.conf

In desperation I also tried dpkg-reconfigure on a list of gnome packages  suggested on one web page, to no avail.

I'd like to avoid a complete reinstall, because I have just finished building this box on Hardy, and don't really want to start again from scratch! Any suggestions will be gratefully appreciated!

John

---

