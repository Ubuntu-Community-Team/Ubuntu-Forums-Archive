---
title: "Blank Boot Screen"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Kale on 2007-10-24
Like many, I recently upgraded to Gutsy. However now i can only boot in recovery mode. When i boot normally the screen goes black. I found a thread that instructed me to edit the script on the main boot sequence (the long one next to recovery mode) and remove "splash", and then boot. This works, however, i would like to know how to make this change permanent so i dont have to edit splash out every time i boot up.

---

### Post by Pumalite on 2007-10-24
Remove it from the kernel boot parameters in your menu.lst

---

### Post by Kale on 2007-10-24
thankssssss that worked great

---

### Post by Pumalite on 2007-10-24
You are welcome. Good luck.

---

