---
title: "Location bar - can't toggle"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Naatan on 2010-04-10
Hi,

I upgraded from 9.10 to 10.04 alpha 3 (at the time) and have never been able to toggle between clickable and manual location bar in Nautilus.. it's always the manual location bar (I have no button to switch between them).

I tried reinstalling Nautilus and deleting ~/.nautilus .. neither worked..

Any ideas?

---

### Post by MacUntu on 2010-04-10
The toggle button is gone, use Ctrl+L to enable the location bar.

---

### Post by Naatan on 2010-04-10
CTRL+L doesn't do anything for me .. it's always stuck in manual mode (ie. its an input field).

---

### Post by MacUntu on 2010-04-10
Start gconf-editor and navigate to '/apps/nautilus/preferences/always_use_location_entry' => set to false.

---

### Post by Naatan on 2010-04-10
Perfect! That did it! :) Thanks a lot MacUntu

---

