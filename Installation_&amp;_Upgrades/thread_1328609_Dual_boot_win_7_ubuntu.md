---
title: "Dual boot win 7 ubuntu"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by carmdg on 2009-11-16
I've just got a new laptop with windows 7 installed and have created a dual boot with ubuntu karmic koala.

However when my grub loads it shows a windows vista and 2 windows 7? Can someone tell me what's the difference between the 2 windows 7, why is there a windows Vista and can I remove some of these options from the grub?

Also where can I find the code for changing the grub to auto load vista, currently im having a much lower battery life in ubuntu. (though I know where the thread is for that) and which win 7 should I set it too?

Thanks

---

### Post by audiomick on 2009-11-16
hallo.
look around on the forum a bit. It seems that Win 7 has a recovery partition that can be removed. I've seen a few posts on the subject, but not paid much attention as I don't have win 7

---

### Post by carmdg on 2009-11-16
would I be stupid to suppose thats the seconds Win 7

---

### Post by audiomick on 2009-11-16
Don't know. Try Booting off the live CD and having a look with gparted. Maybe that will give you  a clue

---

### Post by carmdg on 2009-11-16
right I did that and think its sda3, how do I then set windows as the main load?

thanks for your help audiomick btw!

---

### Post by carmdg on 2009-11-16
I went here, [https://help.ubuntu.com/8.04/switching/dualboot-custom.html#dualboot-custom-bootorder](https://help.ubuntu.com/8.04/switching/dualboot-custom.html#dualboot-custom-bootorder) for the Grub change but my menu.lst is empty? any ideas

---

### Post by carmdg on 2009-11-16
Right in the end I used start up manager to reset the grub load sequence but if any one could help me as to why I couldn't see anything in the menu.lst file I would be grateful

---

