---
title: "Clean Install Help"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by dropslash on 2006-09-25
I was wondering if there was a way to do a clean install of Ubuntu (Breezy).  By this I mean no programs preinstalled, just Ubuntu.  I don't mind the default install I just don't quite understand dependencies and I don't want to delete something that is needed by something else.  Sorry for the comparison (so please don't flame) but in Windows, each program was it's own entity in a way and deleting one meant everything else worked just fine.  In Linux, everything seems dependent on each other.  Very confusing.  Also, if there is a way to do a clean install, will all my hardware work as it does now?  Sorry for all the questions but I have no one around here who knows Linux.  I need your guidance!

Thanks

---

### Post by croak77 on 2006-09-25
Yes. You can do a server install. That will give you a very basic install without X or GNOME. If you want to add X, then you can type;
```

sudo aptitude install x-window-system-core xserver-xorg
```

For a basic GNOME with gdm and synaptic;
```
sudo aptitude install gnome-core gdm synaptic
```

---

