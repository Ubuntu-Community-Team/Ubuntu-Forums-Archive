---
title: "If I installed acroread with dpkg then how to uninstall?"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-24
Used this but I'n not sure how to uninstall it.

```
sudo dpkg -i --force-architecture AdobeReader_enu-8.1.1-1.i386.deb
```

---

### Post by Tibuda on 2009-09-24
Have you tried **sudo dpkg -r** (remove) or **sudo dpkg -P** (purge)?

---

### Post by kansasnoob on 2009-09-24
I'm not 100% sure but since it's a .deb I think you'll see it in Synaptic. Worth a look:confused:

If it's there just mark for complete removal.

---

### Post by Darkshade on 2009-09-24
```
sudo aptitude remove acroread
```
Use purge instead of remove if you want to get rid of everything.

---

### Post by sportjunkie on 2009-09-24
I did that as well. Installed *acroread*, realized *evince* does everything I need and uninstalled *acroread* 

> sudo aptitude remove acroread

only to see that the uninstall isn't removing the mime-type binding to *acroread*. So I had to manually change the pdf related application in most applications (*thunderbird*, *firefox*, *nautilus*). Quite painful task! I greped through [FONT="Courier New"]/etc[/FONT] for *acroread* in hope that I could change it at on central location but grep returned nothing.

---

### Post by philinux on 2009-09-24
> **Darkshade said:**
> ```
sudo aptitude remove acroread
```
Use purge instead of remove if you want to get rid of everything.

I was going to that but it did not mention removing acroread. Anyway went ahead and did it. Seemed to work but left the menu item behind and some leftovers.

locate acroread
/etc/cups/acroread.conf
/opt/Adobe/Reader8/Reader/intellinux/bin/acroread
/opt/Adobe/Reader8/bin/acroread
/usr/bin/acroread
/usr/lib/pymodules/python2.6/orca/scripts/apps/acroread.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/acroread.pyc
/usr/share/pyshared/orca/scripts/apps/acroread.py

---

### Post by rajeev1204 on 2009-09-24
> **philinux said:**
> I was going to that but it did not mention removing acroread. Anyway went ahead and did it. Seemed to work but left the menu item behind and some leftovers.

locate acroread
/etc/cups/acroread.conf
/opt/Adobe/Reader8/Reader/intellinux/bin/acroread
/opt/Adobe/Reader8/bin/acroread
/usr/bin/acroread
/usr/lib/pymodules/python2.6/orca/scripts/apps/acroread.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/acroread.pyc
/usr/share/pyshared/orca/scripts/apps/acroread.py

sudo apt-get purge or aptitude purge instead of remove should do it.
The menu entry will probably require a restart to vanish.

---

