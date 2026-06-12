---
title: "No longer get the option to boot Ubuntu"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by paranoidchampion on 2008-02-15
Hi, I was wondering/hoping!!! that someone can help me out!

I have had Ubuntu and Windows XP working fine using dual boot.  Until today, I had to reinstall Windows XP due to some problems it had developed.  Windows XP now works fine, but the boot menu no longer loads up when I switch on the PC, allowing me to choose between Ubuntu and Windows XP.

Any advice on what to do?

Thanks in advance

---

### Post by luisromangz on 2008-02-15
You should search info about how to reinstall grub.

---

### Post by jimbob on 2008-02-15
Ex Pee overwrote the boot sector on your hard drive.  If you have a stand-alone Linux CD that will give you a terminal window you can start up Grub and repair it.  Assuming that you have only one drive and ex pee is on the first partition and Ubuntu is on the second the commands would be:

grub> root (hd0,1)
grub> setup (hd0)
grub> quit

The forum is rich with solutions as most everyone has had this problem.

---

### Post by paranoidchampion on 2008-02-15
Thanks, I'll look into both of your answers.  I should of thought about researching of how to reinstall grub, unfortunately ... i forgot it was called grub!

Thanks!

---

