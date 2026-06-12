---
title: "Issues with keyboard and mouse at GDM"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Neon Lights on 2009-02-09
ok. So booting up regularly, I get to the GDM login screen...and my mouse won't respond, and nor will my keyboard. NumLock won't even light up. 

Going into the recovery thing, keyboard works. And once (I think I was in a root terminal, and did startx) I got to a gui, but my mouse and keyboard stopped responding. So I decided I'd try alt+Sysrq reisub - and oh wait. Back to a terminal thing before I finished. :P So I'm confused.

what logs should I check, things do I need to reconfigure, etc.? >.<

Dell USB Keyboard, Logitech wireless mouse..

---

### Post by Neon Lights on 2009-02-09
Hrmmm. After messing around a bunch, I got it. o.O
I think restarting dbus, hal, and then GDM did it.

I dunno if it's gonna happen again after I restart. But yeah. -.-

---

### Post by Mazza558 on 2009-02-09
Same problem here. 

Temporarily solved by booting the -6 rather than -7 kernel.

---

### Post by afv on 2009-02-11
Same problem here after installing gdm-new (coincidence or not).

Workaround that worked with me:

1) Alt + SysRq + R
2) Ctrl + Alt + 1 (Login at tty1)
3) sudo /etc/init.d/dbus restart

---

### Post by Mazza558 on 2009-02-11
It's working again now.

---

### Post by Neon Lights on 2009-02-11
Yep, installed a bunch of updates and restarted, violà. :]

---

### Post by Neon Lights on 2009-02-18
Ahhhhh, and it's back again. It appears dbus is not starting, which means HAL doesn't start, and maybe related: Network Manager isn't starting either.

halp?

---

