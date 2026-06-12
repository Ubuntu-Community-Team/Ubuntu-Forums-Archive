---
title: "2ond monitor does not detect, shows out or range"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by darkultra on 2011-02-15
Hi!

My brother got a new 120hz monitor, but can only get the old one to work. If he boots up with both of them connected in windows xp they work fine, but in Ubuntu 10 only the old one works. If he tries to detect the monitor in Display Preferences, nothing happens.

The old monitor is connected to vga output (lcd with vga only) the new monitor is connected to dvi with a dual-link dvi cable. We know the graphics cards cannot provide 120hz, for now we run the monitor at 60hz until he upgrades the rest of the pc (sandy bridge i guess).

The 120hz monitor worked fine until he changed graphics card from a ATI radeon 9200 to a geforce 3 ti 500.

He has tried
sudo dpkg-reconfigure xserver-xorg
and detect monitor in Display Preferences
but no dice.

Could he try restricted drivers?


System specs:
Ubuntu 10.04 32bit
athlon xp 1700mhz
1GB ram
ati radeon 9200
geforce 3 ti 500
lg w2363d

---

### Post by darkultra on 2011-02-26
I went into administration - hardware drivers and got a question if i wanted to install nvidia drivers, i said yes rebooted and now it detects the new monitor and I can run it at native resolution 1920x1080

However the colors are very off, with a lot of yellow. anyone know how I can fix that? The monitor works fine xp dual boot.

---

