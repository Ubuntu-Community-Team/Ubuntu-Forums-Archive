---
title: "Grub loader"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by jflaker on 2007-08-26
I have installed Ubuntu Feisty on a USB drive and it is working great.  

How do I change Grub to show Windows as my default boot OS?

Thanks......should be a simple question.

---

### Post by merlinus on 2007-08-26
Look in /boot/grub/menu.lst 

Count the stanzas down to the windows stanza.

Change the line

default 0

to one less than the number of the windows stanza, since numbering begins at zero.

If you want it to appear first in the grub menu, then you can move that stanza to just above the line

### BEGIN AUTOMAGIC KERNELS LIST

In that case, leave default 0.

-merlin

---

### Post by rzrgenesys187 on 2007-08-26
if you want to have it appear first in the menu im pretty sure you have to edit the grub file (sudo gedit /boot/grub/menu.lst).  I would guess if you moved the windows title (towards the bottom of the file) and the code associated with it to the top that would work.  Hope that helps

---

### Post by flatwombat on 2007-08-26
Open a terminal and type:

> sudo gedit /boot/grub/menu.lst

This will open a new window with your current grub.  Look for 'default=' and then substitute the number there for the number that corresponds to your Windows boot.  Keep in mind that the computer counts up from zero, so your first kernel will be "0", the next one "1" and so forth.  Also, if there are entries that are preceded by a comment (#) they are bypassed by the system and don't 'count'.  Once you've made the change, 'save', close and type 'exit' to leave your terminal, reboot and test.

---

### Post by jflaker on 2007-08-26
Between merlinus and flatwombat, it worked.......Windows is last in the list and is highlighted.......

I appreciate the fast replies!

\\:D/

---

