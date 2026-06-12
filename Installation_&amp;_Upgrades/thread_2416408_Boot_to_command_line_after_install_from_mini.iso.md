---
title: "Boot to command line after install from mini.iso"
date: 2019-04-09
forum: Installation &amp; Upgrades
---

### Post by MarekS on 2019-04-09
After installing Ubuntu from mini.iso on a USB stick, choosing the Xubuntu desktop option, my PC boots to the command line.

How can I get a graphical desktop?

---

### Post by Bashing-om on 2019-04-09
MarekS; Hello -

Setting up a system from Ubuntu mini.iso has a learning curve. :)

to start a installed GUI try terminal command:
```

startxfce4

```
as a 1st for things on the to-do list modifications.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by MarekS on 2019-04-09
Thanks for that.

After
sudo apt install xfce4-session
installed 476Mb

startxfce4
was answered with
/usr/bin/startxfce4/: Starting X server
/usr/bin/startxfce4/: 118: exec: xinit: not found

---

### Post by MarekS on 2019-04-09
Did this:

sudo apt install xinit
startx

And I got a very minimal, almost empty desktop. But now I'm getting there.

---

### Post by Bashing-om on 2019-04-09
MarekS; Welp -

Sticking your head down into the hole.
what is line number 118 in the file " usr/bin/startxfce4" pointing to ?

Bet there is more install and configs to do yet.

maybe have a looksee at:
```

less /etc/xdg/xfce/xinitrc

```

[INDENT][INDENT]make the process to work
[/INDENT][/INDENT]

---

### Post by MarekS on 2019-04-09
> **Bashing-om said:**
> MarekS; Welp -

Sticking your head down into the hole.
what is line number 118 in the file " usr/bin/startxfce4" pointing to ?

Bet there is more install and configs to do yet.

maybe have a looksee at:
```

less /etc/xdg/xfce/xinitrc

```
[INDENT][INDENT]make the process to work
[/INDENT]
[/INDENT]


No such file.

---

### Post by Bashing-om on 2019-04-09
MarekS - :)
> 
And I got a very minimal, almost empty desktop. But now I'm getting there.


You will find there are many paths to "getting there".

A minimal install is just that - ya build your own, installing only what you want.

-all in what you want-

---

