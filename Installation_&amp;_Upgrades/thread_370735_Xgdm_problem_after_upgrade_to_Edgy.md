---
title: "X/gdm problem after upgrade to Edgy"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by f-bomb on 2007-02-26
having a strange problem with X after an upgrade from dapper to edgy.  I simply changed my sources.list to point to the edgy repos and did a sudo apt-get dist-upgrade.  I had my net connection drop while downloading, so I had to run the command again to continue.  Had a conflict with kontact, xffm4-trash and xffm4-recent that was aken care of with an apt-get -f install.  Post upgrade I rebooted and dropped into my familiar GDM login screen.  After logging in, GNOME started to fire up, started rendering the panels, then flickered a couple times and dumped me back to the GDM login screen.  Same happens when I try KDE and Xfce.  I did a dpkg-reconfigure xserver-xorg with no luck and a dpkg-reconfigure --all with no luck as well. 

Can anyone point me in the right direction for diagnosing what's going on and finding a solution other than a clean re-install, as I don't want to move all my data and settings off the box.

Its an old Gateway Performance 500 that ran Hoary, Breezy, and Dapper like a rockstar.
PIII 500Mhz
448 MB RAM
3dfx Voodoo 3 card

---

### Post by renzokuken on 2007-02-26
could you post your xorg.conf?

were you using the official nvidia driver before the upgrade?

---

### Post by f-bomb on 2007-02-26
no, I have an old 3dfx Voodoo 3 card, like I posted above.  it uses the tdfx driver i've diffed the current xorg.conf vs the newly installed on and they are identical except for a few new font paths.  Anyone know of any logs I could look at to try and figure out wtf is happening?

---

### Post by renzokuken on 2007-02-26
try using the "nv" or "vesa" driver instead.........

---

### Post by f-bomb on 2007-02-26
the vesa driver did the trick.  thanks!  btw, the nv driver didn't work.  would crash X.

my question now is: why wouldn't the tdfx driver work anymore?  I'm just curious....

---

### Post by renzokuken on 2007-02-27
were you using the tdfx driver before the upgrade?

personaly ive never even heard of the driver let alone used it........

---

### Post by kingcharles1666 on 2007-02-27
the tdfx driver is broken in edgy
see
 [http://ubuntuforums.org/showthread.php?t=212175](http://ubuntuforums.org/showthread.php?t=212175)

---

