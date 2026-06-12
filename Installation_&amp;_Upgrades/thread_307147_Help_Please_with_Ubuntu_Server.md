---
title: "Help Please with Ubuntu Server"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Intruder on 2006-11-26
Good morning all.....

After recently losing a motherboard im (trying) to reinstall said server..  Installation goes fine, so i move on to adding desktop  (apt-get install ubuntu-desktop) all seems to go ok but when its finished cant startx it trys to load but i get a grey screen and a small terminal window in the top right..  So i end X then im told it needs "dpkg --configure -a "  Which i do seems to get so far and restart....  Anyone any ideas of wots going on? Im a newbie and it has me been messing with it since last night installed OS about 4 times and fedup now..  :-| 
Cheers for looking

Int

---

### Post by taurus on 2006-11-26
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

