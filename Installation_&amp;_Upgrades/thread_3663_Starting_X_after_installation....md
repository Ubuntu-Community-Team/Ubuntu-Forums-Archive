---
title: "Starting X after installation..."
date: 2004-11-08
forum: Installation &amp; Upgrades
---

### Post by FreewheelinFFranklin on 2004-11-08
I just installed Ubuntu on my laptop, and it seems I cannot boot in graphic mode ! The only login I can see is the text-only.  I tried too launch X with startx, but all I get is an error msg...

Any idea ? Did I miss something during installation ?

Nicolas

---

### Post by daniels on 2004-11-08
We'd really need the error message to know any more ... the full error message.  The contents of /var/log/XFree86.0.log would also be handy.

---

### Post by wallijonn on 2004-11-08
If you are at the # prompt,
```
/usr/X11R6/xf86cfg
```

---

### Post by FreewheelinFFranklin on 2004-11-09
Thanks !
I finally re-installed Ubuntu on my machine, and everything is ok !! I am really impressed and I think I found my os.

However, I still encounter some pbl : sometimes my usb mouse stops working, sometimes it is my usb key. Apps are often slow to launch... and I get an error message in the very beginning of the boot :
"MP-BIOS BUG=8254 TIMER NOT CONNECTED TO IO-APIC", and sometimes it is followed by a kernel panic.

Any idea ?

---

