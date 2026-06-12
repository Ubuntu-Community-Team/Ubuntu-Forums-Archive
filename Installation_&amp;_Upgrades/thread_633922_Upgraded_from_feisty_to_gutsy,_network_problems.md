---
title: "Upgraded from feisty to gutsy, network problems"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by The Keeper on 2007-12-07
I had installed Ubuntu Feisty on my parents computer and set up apt-get to update and upgrade during booting by setting up necessary lines in /etc/rc.local. This worked fine until I used the recommended upgrade tool to upgrade to Gutsy.

After upgrade was successfully finished, I noticed that network wouldn't work until gnome had loaded. Network wasn't initialized during boot-up and didn't work in text mode (safe mode), and this also meant that the automatic updates I had set up didn't work either.

Is this a feature in Gutsy or an upgrade bug? Does anyone know how I can restore network functionality during boot-up?

Thank you.

I've tried to search for this problem many times, but either I'm unlucky with searching or I'm the only one with this problem...

---

### Post by PmDematagoda on 2007-12-07
Could you post if:-

```
sudo /etc/init.d/networking start
```

can get you an internet connection in text-mode.

---

### Post by The Keeper on 2007-12-07
That command produced following output:
Ignoring unknown network interface eth0
Ignoring... eth1
Ignoring... eth2
Ignoring... ath0
Ignoring... wlan0
                  [OK]

Network doesn't work afterwards.

---

### Post by The Keeper on 2007-12-09
*bump*

Still need help to solve this, please.

---

