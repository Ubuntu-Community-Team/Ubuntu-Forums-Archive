---
title: "No Xfix in karmic?!?!?"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by qwerty800 on 2009-08-23
Hi!

I just updated my nvidia drivers from 180 to 185.
Everything seemed to work fine.
But when I restarted my computer, I got into a shell.

X can't start: Connection refuser (errno 111)

Well, I'm good at using shell, so not much of a problem there...

But I still need to fix X!

So I go in recovery mode: No Xfix.
I type xfix in a shell: No Xfix.
Look into apt-cache: No Xfix.

Why have you removed such a nice peice of software from Ubuntu?
How am I supposed to fix my problem?

---

### Post by garybrlow on 2009-08-23
Same thing happened a few days ago. The recent update remove dependencies of the nvidia drivers. Just install / reinstall the 185 driver and it will correct the dependency problem. :) Apparently the xfix option is gone. Use the shell with networking option the dependencies need to be uploaded. :)

---

### Post by qwerty800 on 2009-08-23
> **garybrlow said:**
> Same thing happened a few days ago. The recent update remove dependencies of the nvidia drivers. Just install / reinstall the 185 driver and it will correct the dependency problem. :) Apparently the xfix option is gone. Use the shell with networking option the dependencies need to be uploaded. :)

Nope, same thing again!

I wonder if it would be a good idea to change my xorg.conf to some working drvers, like nouveau...

Or maybe reinstall the old version of the propriatary drivers...

---

### Post by dino99 on 2009-08-23
well, try sudo xorg -configure

that create a xorg.conf wich is gone with karmic.
If your problem happen on an upgrade of previous distro, a good solution is to clean as much possible xorg & nvidia ( remove / purge everything about nvidia, and reinstall again)

something wrong in the logs ?

---

### Post by qwerty800 on 2009-08-23
> **dino99 said:**
> well, try sudo xorg -configure

xorg: Command not found

Tried un downgrade the drivers to 180, but they won't install.
The packages are told to have some kind of defect...

---

### Post by dino99 on 2009-08-23
my bad,

Xorg -configure

---

### Post by qwerty800 on 2009-08-23
> **dino99 said:**
> my bad,

Xorg -configure

I dodn't knew that the case could change the way the commands are taken...

Anyway, the same problem still remain.

---

### Post by dino99 on 2009-08-23
what special about that in logs (/var/log) ?

have you tried to clean /autoclean /autoremove the install -f ?
If the 185 file is corrupted, redownload it & reinstall

have you some exotic repositories ( ppa ) ?

Is your sources.list only point to karmic ?

---

### Post by cariboo on 2009-08-23
Start in recovery mode and move your current /etc/X11/xorg.conf to a backup:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then type exit and choose resume from the menu and continue on to your desktop. Once at the desktop reactivate the restricted drivers and restart.

---

### Post by qwerty800 on 2009-08-23
Parse error on line 60 of Xorg.conf
The BusID keyword require a quoted string to follow it.

[QUOTE=Xorg.conf]BusID 01:00.0[/QUOTE]
It make sense, since I manually added this line. Somebody with the same problem did this and it worked.
I'll try to edit that...

EDIT: I did...

Got a kernel panic in midboot...
I think I'll remove this faulty line, since my sistem worked without it...

---

### Post by qwerty800 on 2009-08-23
Well, it seem like this line was the key of the problem...

I just wonder how could this be possible, since the problem started BEFORE I add this line.

Anyway, my problem is resolved, but it still don't awnser my question:

What happened to Xfix?!?!?!?

---

