---
title: "Ubuntu Linux not booting after Online Update"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by dexteer555 on 2010-01-12
I updated my packages online after that, when I restart my laptop, it wont boot up, it just shows "sh grub:" 
I am a newbie and I am using ubuntu by installing Wubi on my XP
Can anyone help??

---

### Post by bcbc on 2010-01-12
search the forums... you are not alone. You'll find many posts on wubi and grub2... I assume the solutions work, but they're not exactly newbie oriented. 

If you haven't made many changes in ubuntu, just boot windows (I assume you can still do this, although you didn't say), go to add-remove programs and remove wubi, and then reinstall it. After that, when ubuntu auto-updates, make sure you deselect anything with grub in it. 

Then if you're really set on using Ubuntu, try switching to a dual boot install for a more permanent solution than wubi.

PS if you don't want to lose your work on wubi, you can also back up the entire ubuntu install (it's just a file - c:\ubuntu\disks\root.disk) and then mount it later and pull off what you need.

---

