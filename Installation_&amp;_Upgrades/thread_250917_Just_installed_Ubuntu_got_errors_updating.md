---
title: "Just installed Ubuntu got errors updating"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by mistergoof on 2006-09-04
I've just installed ubuntu, all went ok
I was prompted on sreen that 163 updates were availble so I let it go for it
when it finished i got the following errors
> E: capplets-data: subprocess post-installation script returned error exit status 134
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gnome-terminal: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

any ideas what went wrong ? why? and what might be done?
TIA

MG

---

### Post by taurus on 2006-09-04
How did you update your Ubuntu?  Did you run it from a prompt with apt-get or aptitude or did you use synaptic?

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by mistergoof on 2006-09-04
I just clicked on the icon on the top tool bar, 
Sy thats all I know

---

### Post by taurus on 2006-09-04
Why don't you run it from a terminal which is not that bad.  Open one with Applications -> Accessories -> Terminal and type in those two commands.  See if you can upgrade your machine that way.

---

### Post by mistergoof on 2006-09-04
ok 

I rebooted and then did
> sudo aptitude upgrade
no errors so I guess al is well

but it would be nice to know what the errors are

PS I cone from a Gentoo background so not affraid af getting hads dirty

---

### Post by taurus on 2006-09-04
Before you run the upgrade command, make sure you run the update first.  Always

```

sudo aptitude update
sudo aptitude upgrade

```

---

