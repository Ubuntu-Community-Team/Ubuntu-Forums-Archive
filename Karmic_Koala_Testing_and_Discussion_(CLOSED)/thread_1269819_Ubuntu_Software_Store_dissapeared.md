---
title: "Ubuntu Software Store dissapeared??"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-09-18
Hello,

I have a fully updated Karmic system, Ubuntu Software Store has seemingly disappeared from the menus, I can't find it, although it is still apparently installed (checked in Synaptic)..

Is this just me or??

Lee Jarratt

---

### Post by LKjell on 2009-09-18
It is located under system.

Tried to run software-store in a terminal?

---

### Post by go7Ul1ai on 2009-09-18
It isn't under system for me or anywhere else, but I can run it from terminal..

Edit: Nevermind, it somehow deselected itself in 'edit menu' ^_^

---

### Post by MacUntu on 2009-09-18
How is that possible? I'd like to remove it from the menu too - "Ubuntu Software Store" makes the menu so ugly wide.

---

### Post by go7Ul1ai on 2009-09-18
> **MacUntu said:**
> How is that possible? I'd like to remove it from the menu too - "Ubuntu Software Store" makes the menu so ugly wide.

Surely you know how to ^_^

Right click the menu bar, then click 'Edit Menus' etc.

---

### Post by SixedUp on 2009-09-18
> **MacUntu said:**
> How is that possible? I'd like to remove it from the menu too - "Ubuntu Software Store" makes the menu so ugly wide.

System -> Preferences -> Main Menu, allows you to disable/enable items in the menu structures.

---

### Post by tekstr1der on 2009-09-18
Saw this change earlier and was confused. Perhaps related to OP:

```
gnome-panel (1:2.27.92-0ubuntu4) karmic; urgency=low

  * debian/patches/01_layout.patch:
    - don't list software-store (lp: #431882)


```

---

### Post by MacUntu on 2009-09-18
Sure I know how to edit the menu entries, but "Ubuntu Software Store" isn't listed. :-k

Edit: Ah, after an update it's now deselected under "Applications" but still I have the entry under "System".

---

### Post by go7Ul1ai on 2009-09-18
> **MacUntu said:**
> Sure I know how to edit the menu entries, but "Ubuntu Software Store" isn't listed. :-k

Mine was located under 'Administration', but still that won't solve your problem if you're trying to remove it from the actual 'System' menu. Mine actually just disappeared from there and moved to 'Administration' after updates.

Lee

---

### Post by tjeremiah on 2009-09-18
i cant find mines anywhere after update. Hide and Seek it is.
Update : Why hide it? It was good where it was before. I had to go to Edit Menu for it to appear again and it now shows under Applications.

---

### Post by MacUntu on 2009-09-18
Nice! I now have it: deselected for "Applications", selected for "System > Administration", and not shown in the editor under "System". Still I'm not buying anything from that store. :P

Do you have both of that files?

/usr/share/app-install/desktop/ubuntu-software-store.desktop
/usr/share/applications/ubuntu-software-store.desktop

Edit:
I created a new user and all entries are gone (for this user)  - guess I have some leftovers. If only the cruft remover would work. :D

---

### Post by mpt on 2009-09-19
> **lee.jarratt said:**
> I have a fully updated Karmic system, Ubuntu Software Store has seemingly disappeared from the menus, I can't find it, although it is still apparently installed (checked in Synaptic)..

Is this just me or??

It’s not just you. We’re halfway through the process of moving it from the “System” menu to the “Applications” menu. Sebastien Bacher has removed it from the “System” menu; now someone needs to unhide it by default in the “Applications” menu.

It’s [a simple packaging bug]("http://launchpad.net/bugs/431882"), if anyone wants to help out.

---

### Post by Robin Nixon on 2009-09-19
> **lee.jarratt said:**
> Mine was located under 'Administration', but still that won't solve your problem if you're trying to remove it from the actual 'System' menu. Mine actually just disappeared from there and moved to 'Administration' after updates.

Lee

That's weird. One of my PCs still has it under System but like you the other had it unselected in the Administration menu. I had to check the box and drag it back to the System menu.

[Edit: Never mind I see it's also under the Applications menu, replacing add/remove]

---

