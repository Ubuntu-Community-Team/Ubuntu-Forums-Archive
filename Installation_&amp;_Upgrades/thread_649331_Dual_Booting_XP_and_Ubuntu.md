---
title: "Dual Booting XP and Ubuntu"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by I_Eat_Childrenz on 2007-12-24
So, I partitioned my 160 Gb hard drive for ubuntu and split it in half exactly. I got ubuntu installed perfectly but now, I cannot boot back into XP..It just says Starting or Booting or something simple like that and thats all it does, it never boots back to XP. I need to go back to xp so I can use my wireless card because I cannot get it to work, But thats another thread. So, any help would be appreicated? Thank you so much,
B.

---

### Post by logos34 on 2007-12-24
> **I_Eat_Childrenz said:**
> So, I partitioned my 160 Gb hard drive for ubuntu and split it in half exactly. I got ubuntu installed perfectly but now, I cannot boot back into XP..It just says Starting or Booting or something simple like that and thats all it does, it never boots back to XP. I need to go back to xp so I can use my wireless card because I cannot get it to work, But thats another thread. So, any help would be appreicated? Thank you so much,
B.

Do you have the XP install cd?

---

### Post by I_Eat_Childrenz on 2007-12-24
Yes I have the install CD.

---

### Post by logos34 on 2007-12-24
try to force checkdsk--it should run automatically the first time you reboot into windows after resizing it.

Boot frm the cd, press 'R' to enter Recovery Console , and at the prompt enter
[B]
chkdisk /r [/B]

(/r option = error checking and attempt to fix bad sectors)

---

### Post by Bandolin on 2007-12-27
Gee, I would have liked to know if that worked for the guy.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

