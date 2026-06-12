---
title: "windows"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by RESmonkey on 2006-06-28
I got Windows on the slave HD, but I get an error everytime I try loading the Windows OS option screen (I hit ENTER on Other OS's: Windows XP/2000/etc) below the Ubuntu options, and it doens't load windows.

What do I edit?  Do i need GRUB?

---

### Post by confused57 on 2006-06-28
If grub is installed on your Ubuntu master drive, this thread may help:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by yamagami on 2006-06-28
GRUB is your boot manager (the software that gives you the selection of OSes on your machine when you boot up.
The menu is controlled by the /boot/grub/menu.lst.

What do you have in your /boot/grub/menu.lst file?
( you can do: > sudo more /boot/grub/menu.lst)

Mine has this entry right at the very bottom (for XP home):

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Obviously the hd0,0 referrs to my primary (and only) hardrive. My laptop came with XP installed before i chucked it to a smaller partition and installed ubuntu.  But it still sees it as the first partition on the disk. 

Harel

---

### Post by RESmonkey on 2006-06-28
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

I know for a fact that there is a windows on the other HD, because when i swap the HD's it loads when windows is on the master.  I know windows is able to load on slave, but don't know why it's not.

---

### Post by RESmonkey on 2006-06-28
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title           Windows NT/2000/XP (loader)
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```

---

### Post by RESmonkey on 2006-06-28
SORRY, I can't find the EDIT button (really)

The slave drive is single partition, HBD1 , if tht helps

---

### Post by confused57 on 2006-06-28
[QUOTE=RESmonkey]```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title           Windows NT/2000/XP (loader)
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```[/QUOTE]
Try booting up with your Ubuntu connected as master and Windows as slave..when your Grub menu opens, highlight the Windows entry and press "e" to edit.  Then try changing the root line from (hd1,1) to (hd1,0), then try booting...if this works it's not permanent, you'll need to go into your /boot/grub/menu.lst & change it to make it permanent.

Just a thought, you may want to go into your bios and make sure your slave drive controller is enabled.

---

### Post by RESmonkey on 2006-06-28
It does boot with Ubuntu as master, and windows as slave (but windows won't boot was the problem)

I tried teh "0" and it worked!  I'm going to edit that file right now.

---

