---
title: "Multimedia keys not working"
date: 2008-07-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2008-07-25
Just did some updates and now it seems that my multimedia keys and all the other fun keys I have on my keyboard no longer work... the only place where they seem to be able to do anything is in the "keyboard shortcuts" dialog. (which isn't much help if they don't work elsewhere).

Anyone else experiencing the same problem?

---

### Post by Nullack on 2008-07-25
You need to identify your keyboard make and model, download the right drivers for it. In my case, a logitech G15, its working all nicely now including pulse audio hook into my keyboard volume control.

---

### Post by BwackNinja on 2008-07-25
odd... actually they do work, just not with numlock on...

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/182704](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/182704) was apparently for this problem in hardy and it was fixed, but I'm experiencing it now though this bug was fixed.

---

### Post by BwackNinja on 2008-07-26
shameless bump :D

Numlock is on initially, and the keys work then, but when numlock is turned off and then back on, they only work when numlock is off.

---

### Post by Coleop on 2008-07-30
I can verify this issue as well.  Intresting you noticed the numlock, I was trying to figure this out last night.  Thanks at least I can use it for now w/o numlock on.

---

### Post by aamukahvi on 2008-08-01
It's true! I turned off NumLock and now the music control keys are working! Never would've thought of that :P

---

### Post by matthewbpt on 2008-08-01
Same thing with me! I've just been trying to solve this, taking numlock off made the multimedia keys work again =S

---

### Post by edv on 2008-08-02
> **BwackNinja said:**
> Just did some updates and now it seems that my multimedia keys and all the other fun keys I have on my keyboard no longer work... the only place where they seem to be able to do anything is in the "keyboard shortcuts" dialog. (which isn't much help if they don't work elsewhere).

Anyone else experiencing the same problem?I'm experiencing the same issue, the keys used to work just fine until an upgrade this or last week. Now the keys only work if numlock is turned off.

```
edv@sangueferro:~$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "xfree86+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+fi"	};
	xkb_geometry  { include "pc(pc105)"	};
};
```

---

### Post by lolcat23 on 2008-08-02
i followed some how-to, but that how-to seemed only to make the g15 lcd screen work.

So i want the keys to work in amarok too, i see alot of posts with lines like "my keys work but [random other stuff]", or answers like "look up keytouch on google" or "download the right drivers", but im a total nub and couldnt figure out keytouch to work, since it didnt have the g15 on the "what keyboard" list. and i installed all packages from synaptic with g15 related things(some probably not needed, like some dev things).

ive read all forum posts which come up on "g15" search, some are how-to's(like the one i followed) but i still dont get it :(

im running xubuntu latest as of today. sorry i dont know what release(heck, i dont even know where to see that)

if there is a nice how-to which is nub friendly about getting the keys to work in amarok. please show it to me :)

[EDIT]

Ive found some amarok scripts, but they arent adding the keys, now i have song, album etc on the LCD, but still no keys

---

