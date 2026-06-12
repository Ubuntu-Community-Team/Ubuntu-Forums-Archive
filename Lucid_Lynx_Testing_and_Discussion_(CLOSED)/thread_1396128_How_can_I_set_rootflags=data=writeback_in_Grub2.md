---
title: "How can I set rootflags=data=writeback in Grub2 ?"
date: 2010-02-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2010-02-01
Basically as title says, trying some ext4 optimizations, can anyone familiar with the new .cfg layout offer some help ?

---

### Post by maheshasolkar on 2010-02-01
You may need to add the flags to /etc/default/grub and then run update-grub as root. More info at:

  [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Regenweald on 2010-02-01
> **maheshasolkar said:**
> You may need to add the flags to /etc/default/grub and then run update-grub as root. More info at:

  [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Exactly what I needed. thanks a lot.

---

