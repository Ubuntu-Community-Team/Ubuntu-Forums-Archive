---
title: "Dual boot - default entry changed after kernel upgrade"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by domi33 on 2006-06-28
Using GRUB for dual boot, I usually start windows by default after 10 sec (because my wife knows only windows). windows is the last entry in menu.lst and pointed as default using the command default +number. The problem is each time the kernel is upgraded, new lines are inserted in menu.lst and of course the default number becomes wrong.
I tried to delete all the savedefault lines except for the windows partition and set 'saved' as parameter for default. saved menu.lst and restarted but the first line is outlined not the windows entry, it is like default parameter was '0'.
Do you know any tip to keep my windows partition as default entry after kernel upgrade ?
Thanks

---

