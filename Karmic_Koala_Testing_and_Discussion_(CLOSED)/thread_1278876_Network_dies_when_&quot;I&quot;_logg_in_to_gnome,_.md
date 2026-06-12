---
title: "Network dies when &quot;I&quot; logg in to gnome, not anyone else"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by honda on 2009-09-30
History: home folder from 9.04, root from clean install from alpha 6 live cd (usb). Two users. Network is wireless using broadcoms prop STA driver, WPA2 psk, "available for all users". 

The network works at startup, if I switch to a text console and login it still works, if I log in to gnome as the other user it still works, if I login as myself noone has network (networkmanager still thinks it is connected and ok, but a ping says "network unreachable", also for an ip on the local network) As soon as I log out from gnome the other users, including myself on the text console, immediately have a working network again.

The problem started a couple of days ago (with some update), no such problems before. 

I really have no idea what could be causing this, any ideas??

---

### Post by honda on 2009-09-30
found out that killing pulsaudio restores network connectivity, for a while, then pulsaudio restarts... any ideas?

---

### Post by honda on 2009-10-02
Ok, there were some stuff in gconf system->pulsaudio only on my account. By deselecting a couple of "enable" variables there, about zeroconf rtp and stuff, pulseaudio started behaving again, ie no network problems.

---

