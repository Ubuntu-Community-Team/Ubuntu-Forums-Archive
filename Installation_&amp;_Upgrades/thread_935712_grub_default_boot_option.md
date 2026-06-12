---
title: "grub default boot option"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by drudogg on 2008-10-01
what do i do in order to change the default boot option in grub?

i am dual booting ubuntu and leopard, and i want leopard to be default, but ubuntu is... just want to know how to change it...

---

### Post by Partyboi2 on 2008-10-02
[[COLOR=Blue]This[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") will explain how to, If you still are stuck post your grub menu.lst
```
cat /boot/grub/menu.lst
```

---

### Post by WWSmith36 on 2008-10-02
You will have to edit /boot/grub/menu.lst
Change the line

default 0

The first entry is 0, second is 1, etc.

---

### Post by crwmike on 2008-10-02
> **WWSmith36 said:**
> You will have to edit /boot/grub/menu.lst
Change the line

default 0

The first entry is 0, second is 1, etc.

Also, the line "Other Operating Systems:" counts as an entry.

---

### Post by drudogg on 2008-10-02
i tried to do gedit /boot/grub/menu.lst but it won't let me save...

---

### Post by Partyboi2 on 2008-10-02
> **drudogg said:**
> i tried to do gedit /boot/grub/menu.lst but it won't let me save...
You need to open gedit with admin rights to modify the file, so in a terminal type
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by drudogg on 2008-10-02
okay, that explains a lot... thank you for that! i was very frustrated with myself, after editing and could not save it.


BTW: i want to opt for the "saved" option so it will boot the last used partition, do i need to do anything other than change the "0" to "saved" in order to activate the "savedefault" feature?

---

### Post by caljohnsmith on 2008-10-02
> **drudogg said:**
> BTW: i want to opt for the "saved" option so it will boot the last used partition, do i need to do anything other than change the "0" to "saved" in order to activate the "savedefault" feature?
Just change the "default 0" to "default saved" and then add "savedefault" to whichever menu entries you want to be saved as the default entry when you boot them; see [the page on "savedefault" at the official Grub website]("http://www.gnu.org/software/grub/manual/html_node/savedefault.html#savedefault") for details, or let me know if you run into problems.

---

### Post by drudogg on 2008-10-09
did this, and it still only defaults to ubuntu.

anything else that i could try?

---

### Post by lumilanis on 2008-10-10
You can aslo move entire text in order which you want if it don't work with putting default 0, or 1... But it should works as that...

For example, if Ubuntu if in first line, you can exchange it's place with other OSs place. It works fine...

---

