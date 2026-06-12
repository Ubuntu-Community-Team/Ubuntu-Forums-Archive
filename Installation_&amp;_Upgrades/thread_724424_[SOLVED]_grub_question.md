---
title: "[SOLVED] grub question"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by daisyfoofpoof on 2008-03-14
i wanna know how to hide the grub menu and by default boot into vista.  i know how to hide the menu (delete the # before hiddenmenu)  but how to i tell it to by default boot into vista?

---

### Post by Pumalite on 2008-03-14
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Diabolis on 2008-03-14
Edit this file, its pretty self explanatory.
```
sudo gedit /boot/grub/menu.lst
```

What you want to edit is this line:
```
default 0
```

change the 0 for the number of the entry that you want to use.

---

### Post by daisyfoofpoof on 2008-03-14
> **Diabolis said:**
> Edit this file, its pretty self explanatory.
```
sudo gedit /boot/grub/menu.lst
```

What you want to edit is this line:
```
default 0
```

change the 0 for the number of the entry that you want to use.

so wait, if my windows vista is the 4th line in the os selector, then i would put in 3 since line one is considered 0.  right?

---

### Post by Pumalite on 2008-03-14
Yes

---

### Post by daisyfoofpoof on 2008-03-14
OK thanks a lot everybody!

---

