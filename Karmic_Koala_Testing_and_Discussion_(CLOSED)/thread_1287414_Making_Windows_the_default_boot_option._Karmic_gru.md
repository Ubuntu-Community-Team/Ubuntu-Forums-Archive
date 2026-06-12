---
title: "Making Windows the default boot option. Karmic grub2"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrismyers on 2009-10-10
The new grub2 system in karmic is a little different to the original grub.

Instead of editing menu.list, we now just rename a file. This is because update-grub processes files in numeric order.

To make Windows the default boot option, open up a terminal & do:

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
```Then do:

```
sudo update-grub
```
Thats it. Reboot to see the change. :)

Cheers.

[SIZE=1]*Of course I know that Ubuntu is the best & why would anyone want to boot to Windows by default - but in some situations it's necessary.*[/SIZE]

---

