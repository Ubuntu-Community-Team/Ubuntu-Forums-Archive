---
title: "GDM crashes since update from Dapper to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Morrolan on 2006-10-26
Hi,
   I've uploaded to Edgy RC1 from Dapper using the "Apt-get" method described on the Ubuntu site.

Everything went fairly well, except when I first tried to boot Edgy.

I get a message which says:

"The greeter application appears to be crashing.  Attempting to use a different one."

It then opens up the old style grey-box GNOME Display Manager.

I have tried completely removing gdm and reinstalling (including removal of /etc/gdm/*) and all to no avail.

I looked at /var/log/installer/syslog, and found the following:

> Removing language-pack-am-base ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
Purging configuration files for language-pack-am-base ...
Removing language-pack-an-base ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
Purging configuration files for language-pack-an-base ...
Removing language-pack-ar-base ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

That repeated about 20 times in the log file.

Also, when I login to a different tty (CTRL+ALT+F2 for example) I get the following:

> Ubuntu 6.10 machine tty2
machine login: morrolan
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
Password:

Once I enter my password it works fine.  This error actually appeared at some point in the upgrade but I can't remember where.

I hope someone can help, as I'm banging my head against the wall now.


Many thanks in advance,
Morrolan

---

### Post by king_arthur on 2006-11-02
Same identical problem here.

You are not alone.. :)

For the moment I have choosen "automatic login" at startup until somebody comes up with a solution.

---

