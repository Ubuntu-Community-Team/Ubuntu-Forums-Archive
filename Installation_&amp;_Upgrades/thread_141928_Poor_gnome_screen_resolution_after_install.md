---
title: "Poor gnome screen resolution after install"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by JeromeDuke on 2006-03-09
Hi, 

I installed Ubuntu 5.10 and when gnome automatically starts up I can only vaguely see the screen - it flickers and as far as I can make out, it only shows part of the left hand side of the full screen.

I can just about log in (not as root though) and can only just make out the applications, places and systems menus. Can I change the resolution depth from here ?

Alternatively, how do I exit gnome to a normal system prompt using the menus I can see or otherwise, or boot it so it doesn't start gnome? Once I've done that, what configuration file should I change ?

I tried installing Debian previously and that had exactly this problem which I fixed by editing the config file: /etc/X11/Xf86Config-4 and changing the depth and resolution. Is that the same file for gnome on ubuntu ? Debian also had a mouse pointer problem which is why I gave up on it, but from what I can see, the mouse pointer is behaving correctly on ubuntu.

Many thanks for any help.

---

### Post by cilynx on 2006-03-09
/etc/X11/xorg.conf is the file you're looking for.

The syntax is practically identical to the XFree config

---

### Post by Perfect Storm on 2006-03-09
Aye you can do the same in ubuntu as you did in debian.

```
sudo gedit /etc/X11/xorg.conf
```

Edit: cilynx beat me to it.

---

### Post by JeromeDuke on 2006-03-09
Thanks for pointing me to the correct file.

The problem is I can't see enough of the screen to work out how to exit gnome ! i.e. how can I start linux without gnome starting so I'm at a command prompt and can edit the file ?

---

### Post by Perfect Storm on 2006-03-09
After bios run and you see the 3-2-1 countdown press <esc>, then choose failsafe options.
After ubuntu loads you'll be in commands instead.
Then you can edit the xorg.conf from there. (with nano, vim etc. the one you prefer) eg.

sudo nano /etc/X11/xorg.conf.

---

### Post by cilynx on 2006-03-09
Ctrl + Alt + F1 is a nice way to drop to a console with X running

---

### Post by JeromeDuke on 2006-03-09
Great, that did the trick - I restarted, hit escape (which I didn't see before) and changed the depth in the config from 24 to 16 and it fits the screen and is clear (although there are a few small unidentifiable squares of black dots/lines that appear on some applications). I can live with them for now. 

My next problem with this install is mounting a floppy - I ran:
 
mount -t msdos /dev/fd0 /mnt/floppy 

and it returns the error:

mount: special device /dev/fd0 does not exist

Has it not detected my floppy drive ?

Thanks.

---

### Post by AndrewCaul on 2006-03-09
[QUOTE=JeromeDuke]
My next problem with this install is mounting a floppy - I ran:
 
mount -t msdos /dev/fd0 /mnt/floppy 

and it returns the error:

mount: special device /dev/fd0 does not exist

Has it not detected my floppy drive ?

Thanks.[/QUOTE]
That's what it looks like. I'm pretty sure /dev/fd0 is the floppy drive.

---

### Post by JeromeDuke on 2006-03-10
Yes, I think so too. Anyone know how to get it detected ?

If I look in /dev I can see a directory called "fd:" and what appears to be subdiectories 0 1 2 etc., but I can't look into them.

---

