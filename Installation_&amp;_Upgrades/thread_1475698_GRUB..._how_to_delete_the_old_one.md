---
title: "GRUB... how to delete the old one?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by w2no on 2010-05-07
i installed lucid into windows.  when i boot then i choose ubuntu and now i ve two kinds in GRUB...
1. Ubuntu, Linux 2.6.32.22 gen - plus the recovery
2. Ubuntu, Linux 2.6.32.21 gen - plus the recovery.
because i just updated it.

how can i delete the ...21?  pls advise.
thanks

---

### Post by dino99 on 2010-05-07
goto synaptic and right click on that package to purging it

---

### Post by w2no on 2010-05-08
dino, big thanks. i found it. now i m trying it out

---

### Post by azertyh on 2010-05-08
many people advise to not remove the previous kernel in case of issues with the last kernel.

---

### Post by wieman01 on 2010-05-08
> **azertyh said:**
> many people advise to not remove the previous kernel in case of issues with the last kernel.
I have never had to go back to previous versions, but yes, it's possible.

---

### Post by AnonCat on 2010-05-08
If someone doesn't want to actually remove the kernel, but rather just it's listing in the grub menu, you can delete the kernel's entry at the bottom of the menu.lst file.  To open the file type the following:

sudo /boot/grub/menu.lst

Just make sure to double-check that you're deleting the right one!

---

### Post by wieman01 on 2010-05-09
> **AnonCat said:**
> If someone doesn't want to actually remove the kernel, but rather just it's listing in the grub menu, you can delete the kernel's entry at the bottom of the menu.lst file.  To open the file type the following:

sudo /boot/grub/menu.lst

Just make sure to double-check that you're deleting the right one!
Problem with this approach is that this file will be overwritten every time a new kernel is installed. So it's only a temporary solution... You can do it though.

---

