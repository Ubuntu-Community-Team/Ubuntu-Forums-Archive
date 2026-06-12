---
title: "Networking issues on desktop and laptop after upgrading 9.04 to 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by veraction on 2009-11-15
[COLOR="Red"][SOLVED][/COLOR] Downgraded to 9.04 and everything works great again. Networking and sound.

I upgraded both systems at the same time and am receiving networking problems.

Desktop: Acer Aspire AX1200-U1520A
Laptop: Toshiba Satellite L25-S119

On the desktop:
[LIST]
[*]When I try to connect to a game I play, it can take 60+ minutes to obtain a connection. In 9.04 it took 30 seconds max.
[*]When I launch wireshark (the one in repos or the latest compiled one), and begin a capture on eth0, my entire system locks up. After restarting, the mouse/keyboard completely lock up right before the login screen. I eventually discovered that waiting 3-5 minutes will cause the mouse/keyboard to unlock. If I don't wait those 3 minutes, I can reboot forever and each time it locks up.
[/LIST]
(I also had static on my audio if 2+ audio players were running simultaneously. Uninstalling pulseaudio fixed that, but I now no longer have any volume controls in Gnome) 

Laptop:
[LIST]
[*]Wired connection doesn't work at all.
[*]Wireless connection has packet loss rates of 90% or higher
[/LIST]

I'll soon be reinstalling 9.04 to confirm that my networking worked flawlessly in that version. But, I would eventually like to upgrade, if anyone has any suggestions.

---

