---
title: "Edit"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by stanley82 on 2008-05-02
Hi, my mouse has not worked on my older PC since feisty so I'm stiil usilng edgy on that machine.  I found a possible fix on thread 4141123 and I'm in the middle of installing hardy on that machine without a mouse.  I've done (ctrl-alt-F1) and I'm in a sort of full screen terminal and I need to edit a file that may fix things for good.

sudo edit /etc/X11/xorg.conf returns 
Warning: unknow mime-type for "xorg.conf" --using "application/*"
Error: no "Edit" mailcap rules found for type "application/*"


can anyone figure out what I should do to get round this one?  I've tried gedit but it is not able to open a display.
          Regards Ian.

---

### Post by sisco311 on 2008-05-02
```
sudo nano /etc/X11/xorg.conf
```Ctrl+o(Enter(Return)) = save
Ctrl+x = exit

---

### Post by stanley82 on 2008-05-02
Great thanks Ian.

---

