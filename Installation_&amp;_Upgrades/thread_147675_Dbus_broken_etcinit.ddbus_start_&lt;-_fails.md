---
title: "Dbus broken? /etc/init.d/dbus start &lt;- fails?"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by xplode_me on 2006-03-20
I searched the foruns, havent found an answer...


When i try do start "/etc/init.d/dbus start" i get this:

joel@supernova:~$ sudo /etc/init.d/dbus start
 * Starting system message bus dbus                                                                                                                  [ ok ]
 * Starting Hardware abstraction layer hald run-parts: /etc/dbus-1/event.d/20hal exited with return code 1


Does anyone know what this means? :( Dbus doesnt start as u can see!

Please help!
Tnkx!

---

### Post by mlind on 2006-03-20
```

mlind@sandbox:~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                              [ ok ]
 * Stopping system message bus dbus                                      [ ok ]
 * Starting system message bus dbus                                      [ ok ]
 * Starting Hardware abstraction layer hald                              [ ok ]

```

seem to work fine here :confused: 
That's pretty serious flaw if you dbus doesn't run for you..

---

### Post by xplode_me on 2006-03-21
[QUOTE=mlind]```

mlind@sandbox:~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                              [ ok ]
 * Stopping system message bus dbus                                      [ ok ]
 * Starting system message bus dbus                                      [ ok ]
 * Starting Hardware abstraction layer hald                              [ ok ]

```

seem to work fine here :confused: 
That's pretty serious flaw if you dbus doesn't run for you..[/QUOTE]


Im gettin this:

```
joel@supernova:~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                              [ ok ]
 * Stopping system message bus dbus                                      [ ok ]
 * Starting system message bus dbus                                      [ ok ]
 * Starting Hardware abstraction layer hald run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
joel@supernova:~$

```

---

### Post by mlind on 2006-03-21
You should definetly file a bug about it and include your system specs too.
Does *dmesg* or */var/log/messages* show anything about HAL failure?

---

### Post by xplode_me on 2006-03-21
They don't :(

---

### Post by Aero Leviathan on 2006-03-30
I'm also having dbus problems in dapper. I get a message on GNOME startup, power manager complains about dbus, and tells me to do this:
 eval `dbus-launch --auto-syntax`
...which does nothing. No output at all.

After reading this post, I tried the following:
aero@woglinde:~$ sudo /etc/init.d/dbus restart
Password:
 * Stopping Hardware abstraction layer hald                              [ ok ]
 * Stopping system message bus dbus                                      [ ok ]
 * Starting system message bus dbus                                      [ ok ]
 * Starting Hardware abstraction layer hald run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
aero@woglinde:~$

I'm a noob so I don't really know what dbus is... the only negative effects for me seem to be that annoying power manager error on start, and also that Epiphany won't run at all... or maybe that isn't related...: 'unable to determine the address of the message bus'

'dmesg | grep hal' and 'cat /var/log/messages | grep hal' (i know, bad cat, i can never remember which way the pointy brackets go) both turn up nothing.

Oh, by the way, I dist-upgraded from breezy, on which I didn't have this problem. I'm not complaining, I know this is what I get for using an alpha.. just thought I'd see if anyone knew what was up :)

Do we still have no ideas about this? This bug-filing business kinda intimidates me...

---

### Post by GrammatonCleric on 2006-05-29
Same here... I recently upgraded using the apt-get dist-upgrade method.  I was forced to reinstall breezy.

It would be interesting to see if any hardware is the same.

AMD 3700+
ABIT NF4ST Mainboard
2gig Ram
320gig WD HD
NEC DVDRW 3520AW
GeForce 6800 GS 256MB PCI-Express
Creative Audigy2

---

### Post by mlind on 2006-05-30
Have you all upgraded from Breezy? Sometimes just removing packages using
--purge and then reinstall those back can help.

---

### Post by GrammatonCleric on 2006-05-30
I did but then I also did  fresh installs from cd using latest dapper rc for the amd64 and then x86.  I did not have the issue to start but after several reboots the hal started failing. So I don't know if I would limit the issue to just upgrading from Breezy.  That's why I started thinking hardware issue.

---

