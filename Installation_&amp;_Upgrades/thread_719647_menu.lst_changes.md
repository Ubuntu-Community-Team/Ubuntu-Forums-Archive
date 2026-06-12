---
title: "menu.lst changes"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by johnykat on 2008-03-09
Every time there is a kernel update menu.lst gets updated to reflect the update. However, I am the only user that uses the Ubuntu partition and I have changed menu.lst so that Windows will boot by default because the other users in the household would be clueless as to what to do to get to the Windows partition. I find myself regularly fixing menu.lst so that Windows goes first, is there a way to force Ubuntu to always put Windows first even after an update that causes menu.lst to be updated?

thank you,

John Pittman

---

### Post by Pumalite on 2008-03-09
First fix #groot permanently. Second, 'default 0' means that Ubuntu will boot first if it is first in the list. Change that to the place that Windows occupies in you menu.lst, keeping in mind that Grub starts counting from 0

---

### Post by vikasmk on 2008-03-09
ya, i faced the sam problem. I have to keep changing the menu.lst file every time .

---

### Post by confused57 on 2008-03-09
> **johnykat said:**
> Every time there is a kernel update menu.lst gets updated to reflect the update. However, I am the only user that uses the Ubuntu partition and I have changed menu.lst so that Windows will boot by default because the other users in the household would be clueless as to what to do to get to the Windows partition. I find myself regularly fixing menu.lst so that Windows goes first, is there a way to force Ubuntu to always put Windows first even after an update that causes menu.lst to be updated?

thank you,

John Pittman
See the section here about pasting your Windows entry above the line  ###BEGIN AUTOMAGIC KERNELS LIST:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

