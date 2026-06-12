---
title: "Can't upgrade from 19.04 to 20.04"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by mcsheffrey on 2020-08-11
Getting message "an upgrade from disco to focal is not supported with this tool'. Also tried [COLOR=#4F4F4F][FONT=&quot]‘do-release-upgrade’ same thing.[/FONT][/COLOR]

---

### Post by Rex Bouwense on 2020-08-11
To upgrade from 19.04 to 20.04, one must first upgrade to 19.10 and then to 20.04.

---

### Post by dino99 on 2020-08-11
Doing a fresh install is the best choice (be sure to save your data first, but i suppose you are using a separate /home partition, so you are safe). Simply select 'manual install' (or so))

Note that by default now ubuntu use a /home repository inside / (root), so if you want to continue with the previous /home partition, then follow the manual install.

Other dirty solution: edit /etc/apt/sources.list and change the release name to focal and save (but first deactivate all third party source, like ppa, and downgrade some packages if needed to avoid conflicts). Then load synaptic (if using gnome DE) and update; then upgrade in that order: gcc/python, metapackages,librairies, and apps.

---

### Post by Rex Bouwense on 2020-08-11
Just realized that 19.10 has also reached EOL.  dino99 gave excellent advise.  Your best, quickest, and easiest course of action is to perform a fresh install after saving your data.

---

### Post by slickymaster on 2020-08-11
*Thread moved to **Installation & Upgrades**.*

---

### Post by mcsheffrey on 2020-08-11
I'm using a dual boot alongside of Windows 10, so I may need to go the dirty route. Thanks for the feedback.

---

### Post by Impavidus on 2020-08-12
Dual booting with Windows shouldn't affect your decision to take either the clean or the dirty route. It's probably best to take the clean route.

---

