---
title: "ifrename"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by jchau on 2006-06-09
On system startup, the system complains:
> /etc/init.d/ifrename: line 12: /sbin/ifrename: No such file or directory

So I check to see if the ifrename package is installed. It isn't, but it conflicts with many of the packages already installed.  I suspect that this problem exists because the install aborted (does anyone know how to finish an aborted install yet?).

What should I do? Should I remove the script or should I install the package & remove the conflicting ones:
[LIST]
[*]gnome-power-manager
[*]gnome-session
[*]gnome-volume-manager
[*]hal
[*]hal-device-manager
[*]hwdb-client
[*]lvm-common
[*]lvm2
[*]mdadm
[*]pcmciautils
[*]ubuntu-base
[*]ubuntu-desktop
[*]ubuntu-minimal
[*]ubuntu-standard
[*]udev
[*]update-notifier
[/LIST]

---

### Post by jchau on 2006-06-20
I still haven't gotten any response, so I'd like to bump this thread up.  It bugs me everytime I boot.  Thanks.

---

### Post by jmr on 2006-06-20
I suspect ifrename is now obsolete.  I think I read somewhere that its function is now done by udev.  Same thing with hotplug.  The Dependencies of the udev package (which you can check with synaptic, e.g.) state clearly:
```
Replaces: hotplug
Replaces: ifrename

```

So, simply remove ifrename.

Now, if your installation did not complete I guess you will bump into other obstacles pretty soon.  Using synaptic to find and fix "Broken" packages might help, but I would feel more confortable doing a clean install from scratch (I suspect you upgraded, right?).  I tried upgrading but got the feeling there was stuff missing.  Actually, in one upgaded computer I could not find the "Printing" configuration tool in the System->Administration Menu.  I decided then to install from scratch.  No problems since.

João Rodrigues

---

