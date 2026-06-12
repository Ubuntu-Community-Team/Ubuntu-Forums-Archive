---
title: "Gutsy No Boot"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by mgaskell on 2007-11-20
Hi all-

I've had Gutsy on my laptop for some time with no problems. Today I tried to load two instances on Firefox, on one a separate desktop using Compiz Fusion. Firefox froze and I had to force quit to get control back. Now my machine will no longer boot into an X session. It only gets as far as the blank X screen with a cursor and goes no further. What files could be corrupted? I can boot to the recovery command line but I don't know what files to look at and what to fix.

Any help greatly appreciated.  Thanks

---

### Post by confused57 on 2007-11-20
> **mgaskell said:**
> Hi all-

I've had Gutsy on my laptop for some time with no problems. Today I tried to load two instances on Firefox, on one a separate desktop using Compiz Fusion. Firefox froze and I had to force quit to get control back. Now my machine will no longer boot into an X session. It only gets as far as the blank X screen with a cursor and goes no further. What files could be corrupted? I can boot to the recovery command line but I don't know what files to look at and what to fix.

Any help greatly appreciated.  Thanks
You can try booting into recovery mode and enter:
```
dpkg-reconfigure xserver-xorg
```
You can probably select "No" to autodetect, then go with the defaults, except select "vesa" as the video driver...this may at least get you to a desktop.  When it's xorg is reconfigured, enter "reboot", without quotes.

You can also change to "vesa" manually:
```
cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf
```
page down to the video driver section and manually type in "vesa", with quotes.
Ctrl+X, y, enter...this will save the changes.

---

