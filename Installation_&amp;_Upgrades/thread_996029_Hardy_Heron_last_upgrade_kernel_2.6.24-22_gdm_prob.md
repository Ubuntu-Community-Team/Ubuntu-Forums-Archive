---
title: "Hardy Heron last upgrade kernel 2.6.24-22 gdm problems"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by eskimo on 2008-11-28
Hi to you all, i've a HP Pavilion 6870 with ubuntu hardy heron installed. After last upgrade (this morning) i've changed in menu.lst the links to te new kernel (i've choose use original menu grub file after installation) but now the graphical sistem can't start, in syslog i've found:

gdm[6111]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' faiiled

what can i do? i'm using kernel 2.6.24-21 because i haven't problem with this...
thanks, Paolo

---

### Post by eskimo on 2008-11-29
up! no one has an idea?

---

### Post by wolfdale on 2008-11-29
I had a similar problem when I upgraded to "-22", after I login, I just got a white screen. I realized my graphic server was having problems with the upgrade so I booted back to my previous version "-21". Un-installed my ATI driver. Re-booted into "-22" which did work this time and then re-installed my ATI driver (using Envy) while logged in to the "-22" kernal. I rebooted a third time, to get "-22" and ATI drivers loaded and it all worked.

---

### Post by michiedo on 2008-11-29
not sure if it's the same problem you're  experiencig (i'm on kde !), but ...
on one computer, after upgrading to -22, kdm was not longer starting (it used 99% cpu forever)
i didn't do much trouble shooting, simply restored /etc/X11/xorg,cong fom my beloved backup and all is working fine now.

on a second pc the upgrade to -22 worked flawlessly.

Auguri, Paolo :-)

---

### Post by blackhole82 on 2008-11-30
Mine is doing the same thing with the white screen.  I also have ati drivers installed.  I guess I will have to boot the previous kernel and go through the same process.

---

