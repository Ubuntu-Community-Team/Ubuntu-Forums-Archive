---
title: "Grub boot menu"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Vrekk on 2008-06-09
Hey i  have ubuntu installed on 2 computers.  My laptop, were it is the  only os, and my desktop, were i dual boot with ubuntu and windows xp pro sp3.  Well on the laptop, when i start it up i get a screen saying Grub loading 1.5 Press esc to got to menu, the boot up fine.well on my desktop i got stright to the menu and i choses ubuntu after 8 secs.  Is there a way to make it the same as with my laptop? Thanks in advance

---

### Post by Vivaldi Gloria on 2008-06-09
You change boot options by editing the file

```
/boot/grub/menu.lst
```

Press Alt+F2 and type

```
gksudo gedit /boot/grub/menu.lst
```

to edit it. The lines with # at the beginning are ignored. So change the line

```
# hiddenmenu
```

to

```
hiddenmenu 
```

to get rid of the menu.

You can also change the 

```
timeout		3
```

to make that wait at the beginning shorter or longer.

---

### Post by Vrekk on 2008-06-09
sweet thanks

---

