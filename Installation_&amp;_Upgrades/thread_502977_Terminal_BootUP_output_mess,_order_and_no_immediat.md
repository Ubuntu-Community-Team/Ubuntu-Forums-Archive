---
title: "Terminal BootUP output mess, order and no immediate login prompt"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by zimso on 2007-07-17
Hello,

I installed Feisty, everything is ok but what I dislike is, when I boot ubuntu, at the end
part of the boot process the output gets confussing. I mean it prints, kernel messages then
again Script messages then the tty1 Login prompt (which should come at the very end)
and then some other script messages and at the end you get the last script message and nothing.
When you press <return> you get the tty1 Login prompt again and you can login.
Maybe someone can help me bring some more order in it ?
Can I change this to hae a more ordered look ?
I stoped the gdm daemon to have console login at start...

Maybe someone can help me ?

Thanks !
Tim

Example:

:
:
 * Loading kernel modules...
 * Loading manual drivers...
     lp0: using parport........ <----- Kernel message inbetween
:
:

 * Setting up console font and keymap...
 * Loading ACPI modules...
Ubuntu 7.04 stift tty1   <-------------- TTY1 Login prompt but it's not finished yet sadly !

peter login:

* Starting ACPI services...

* Starting system log daemon...

* Doing Wacom setup...

* Starting kernel log...

* Starting system message bus dbus

:
:

* Running local boot scripts (/etc/rc.local) <----------------- End state. When I press <return> I get the Login

Ubuntu 7.04 stift tty1

peter login:

---

