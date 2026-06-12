---
title: "Can't find my XP partition!"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Goodkimchee on 2007-04-26
I installed Ubuntu Feisty in a smaller partition on my 60g HD, leaving 40 for XP (which was there first).  The idea being that I would dual boot.  But now GRUB (?) doesn't see XP and just boots into Ubuntu, which I'm sure is fine but I'd really like to have that XP partition & XP when I need it!  Can anyone help?  I'm a bit of a n00b with Ubuntu but don't be hatin'!

---

### Post by beaudoin996 on 2007-04-26
Do you see your partition with gparted ?

---

### Post by Goodkimchee on 2007-04-26
what's gparted?

---

### Post by beaudoin996 on 2007-04-26
> **Goodkimchee said:**
> what's gparted?

Go to this link

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Try to burn the live CD and boot from it

---

### Post by confused57 on 2007-04-26
> **Goodkimchee said:**
> I installed Ubuntu Feisty in a smaller partition on my 60g HD, leaving 40 for XP (which was there first).  The idea being that I would dual boot.  But now GRUB (?) doesn't see XP and just boots into Ubuntu, which I'm sure is fine but I'd really like to have that XP partition & XP when I need it!  Can anyone help?  I'm a bit of a n00b with Ubuntu but don't be hatin'!
Open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

post the ouput of this command

If Windows is on your first partition, you could just add an entry to your menu.lst file to boot it. e.g.

```
cd /boot/grub
```
changes to the grub directory

```
sudo cp menu.lst menu.lst_backup
```
this creates a backup of your menu.lst

```
gksudo gedit menu.lst
```
this opens your menu.lst in the text editor gedit

then add something like this to the very end of the file:
```
title    Windows  XP
root   (hd0,0)
savedefault
makeactive
chainloader  +1
```

It would be best to copy & paste commands(menu.lst is short for menu.list) to avoid typing errors, until you get more proficient with Linux.

Added:  I'm assuming your problem is that you can't boot into Windows from grub.

---

