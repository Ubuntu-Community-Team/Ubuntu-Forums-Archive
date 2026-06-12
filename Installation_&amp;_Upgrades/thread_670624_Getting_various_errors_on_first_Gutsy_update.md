---
title: "Getting various errors on first Gutsy update"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by wheezer on 2008-01-17
Being fed up with all the problems with the Fiesty>Gutsy upgrade, I finally jsut chucked it and installed Gutsy clean... BUT

While everything seemed to install, during the first system update, I got a bunch of errors at the very end, including these, rougly (precise dialog image attached)

E:Caplets-data: Subprocess stopped
E:Gnome-control-center: Dependency Problems
E:Gnome-session: Same
E:Gnome-panel: Dependency Problems (Leaving unconfigured

I can't find discussion of this. Is it serious? Do I just ignore this? Can I fix somehow?

---

### Post by Partyboi2 on 2008-01-17
Open a terminal (Applications>Accessories>Terminal)
and try
```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install -f
```

---

### Post by wheezer on 2008-01-18
> **Partyboi2 said:**
> Open a terminal (Applications>Accessories>Terminal)
and try
```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install -f
```


Thank you partyboi, I've had many updates since then, so that seems to have done nothing at this point.  Can you tell me what that was actually doing? Should I do that after any Live CD build routinely, or just when there's some error?

---

### Post by Partyboi2 on 2008-01-18
apt-get update reloads the package index and 
synchronizes it with the source, which in our case is the ubuntu repositories. Same as the "reload" button in Synaptic Package Manager
apt-get upgrade installs the newest version of packages. Same as "Mark all upgrades" button in Synaptic Package Manager
apt-get install -f will attempt to fix broken packages. Same as "Fix broken packages" under "edit" of Synaptic Package Manager
to read more you can in a terminal type
```
man apt-get
```With running these commands in a terminal they may fix the problem or give  a bit more information on what might be causing the problem.
What happens if you try reinstall Caplets-data?
```
sudo apt-get install --reinstall caplets-data
```

---

