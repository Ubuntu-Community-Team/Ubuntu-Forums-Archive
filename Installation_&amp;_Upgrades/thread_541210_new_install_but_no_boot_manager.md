---
title: "new install but no boot manager"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by goldtech on 2007-09-02
Just installed Ubuntu. 

When I restarted I got only my pre-existing WinXp boot. There was no dual boot, no boot manager to give me a choice.

Please give me simple, step by step instructions to fix this. The Ubuntu install's there but there's no boot for it.

Thanks very much,
LeeG

---

### Post by merlinus on 2007-09-02
Boot from live cd, open a terminal and enter these commands, one at a time, and press Enter after each one.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

Remove live cd and restart.

-merlin

---

### Post by goldtech on 2007-09-02
Did all you said. Still only standard XP boot, no boot manager.

> find /boot/grub/stage1

gave me:  hd0,0

> root (hd0,0)

gave me a no error message, just a return to the command prompt

> setup (hd0,0)

gave me a bunch of good looking config output - I did not write it down - seemed to sucessfully complete.

Still no boot manager. What to try next?

Note, I have two HDs maybe that's a factor?

---

### Post by Pumalite on 2007-09-02
Boot from Live CD
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by merlinus on 2007-09-02
You should have entered:

setup hd(0)

NOT

setup (hd0,0)

Also, before trying cat /boot/grub/menu.lst when booting from live cd, make sure to first mount your ubuntu partition.

You may also have to navigate to its mountpoint first.

-merlin

---

