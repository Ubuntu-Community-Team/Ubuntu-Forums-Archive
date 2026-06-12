---
title: "Managing boot menu"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by port50side on 2007-09-14
I have a solid dual boot system of Windows XP and Feisty 7.04.

I am looking for a way to edit the  boot menu to make XP the default choice and to alter the time given to make a selection.

Regards

---

### Post by dabl on 2007-09-14
Here's all kinds of Grub How-To resources: [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

The Grub timeout period is a number of seconds (default is 10) that appears near the top of the menu.lst file and looks like this:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```

To default to a Windows boot, I would assume you would simply move Windows to the #1 position in the sequence of OS's, but I haven't actually done it -- better review the guidance in the link above.

As for the editing process, for Ubuntu you enter```
 gksu gedit /boot/grub/menu.lst
``` and have at it!  :)

---

### Post by Pumalite on 2007-09-14
Grub starts counting from Zero:

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0


As it is; this allows Ubuntu to be the default.
If Windows is, let's say 4th in your menu.lst then make:


default         3

---

### Post by dabl on 2007-09-14
Ahhhhhhhhhh -- good catch, Pumalite!  :KS

---

### Post by Pumalite on 2007-09-14
Hey dabl, what's up man!

---

