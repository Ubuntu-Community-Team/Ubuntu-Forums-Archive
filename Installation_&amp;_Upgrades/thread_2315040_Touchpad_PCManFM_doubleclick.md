---
title: "Touchpad PCManFM doubleclick"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by rolandskokins on 2016-02-25
Hello to Ubuntu community. I recently installed Lubuntu 14.04 on my Dell Latitude D620. I had some issues, but almoust all I resolve my self except one:
My laptop touchpad wont open file/folder on double click, with buttons its working, scrolling works fine. I found that i need triple click on my touchpad to open file/folder in PCManFM. I have on my D620: AlpsPS/2 ALPS DualPoint TouchPad. Maybe someone know resolution to change PCManFM triple click to double click, in other application touchpad work fine, so i think problem is in PCManFM configuration with my touchpad device.

Update: (problem solved)

Solution is simple, PCManFM use GTK2 toolkit, so we need adjust/create settings doing this:
1.In you home directory edit or create file ".gtkrc-2.0"
2.Then put at the end following line "gtk-double-click-time=500" then save
3.Logout and Log back

---

