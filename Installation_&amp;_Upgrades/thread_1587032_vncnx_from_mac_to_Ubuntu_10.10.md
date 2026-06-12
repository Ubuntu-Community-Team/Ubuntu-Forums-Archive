---
title: "vnc/nx from mac to Ubuntu 10.10"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by smocksturr on 2010-10-02
Hello,

I just set up a headless server in my living room running 10.10, the release candidate.

Everything works great, except for remote access.  Using either VNC or NX (installed NXserver on the server) from either my Macbook (10.6) or my iBook (10.4), the keyboard seems screwed up in the viewing session.  When I press D, everything minimizes, for example.  I can get around this by holding down Option... Is there a setting screwed up somewhere?  I tried setting the keyboard layout to Mac to no effect.

Thanks,

Drew

---

### Post by csogilvie on 2010-10-13
I have the exact same problem.

The letter "d" minimizes ALL of my desktop windows.

I'm using vnc4server.

I remember during the last release upgrade there was a similar issue with a mis-mapped "s" and "m" characters.  (Can't remember the case)

Tragically I seem to remember it took about 1 week for this bug to get resolved.

Anybody else know what to do about this?

I'm running vnc4server on my linux box and regardless of how I access the vnc session (pc or mac) usage of the letter "d" makes the current window minimize.  This is super annoying if you are trying to type in "sudo" or "gksudo"

---

### Post by faber_x on 2010-10-25
I found a workaround in 

[https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/655886](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/655886)
(reply #3)

Quote:
"Fix: I have no idea how or why this happens, but after upgrade to 10.10, a keyboard shortcut is set to make 'D' minimize all windows. After logging in, you can select the menu 'System' -> 'Preferences' -> 'Keyboard Shortcuts' and find the "Hide all normal windows and set focus to desktop" and set this to something sane like "Alt + D".

I suspect that the default is "Mod4+D" and when a system does not have a "Mod4" key available, it drops the modifier."

Hope it helps 

- Faber

---

### Post by exXplode on 2011-01-12
> **faber_x said:**
> after upgrade to 10.10, a keyboard shortcut is set to make 'D' minimize all windows. After logging in, you can select the menu 'System' -> 'Preferences' -> 'Keyboard Shortcuts' and find the "Hide all normal windows and set focus to desktop" and set this to something sane like "Alt + D".

Thanks, that helped!

---

### Post by dwalker109 on 2012-02-29
Super, thanks very much - fixed! (or worked around, at least ;) )

---

### Post by oldos2er on 2012-02-29
Closed, necromancy.

---

