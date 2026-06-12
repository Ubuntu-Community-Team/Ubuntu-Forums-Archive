---
title: "Synaptic package manager/Update Manager Fail"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by geraldbrent on 2011-01-13
E: Type 'nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.

The above is the console output when i type sudo apt-get update

Update manager throws the same error so now I can't install or update software :(:(:( Help me! :confused:

[RIGHT]-gerald[/RIGHT]

---

### Post by oldos2er on 2011-01-13
```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
``` Delete the text, and add 

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

Save and exit, retry ```
sudo apt-get update
```

---

### Post by geraldbrent on 2011-01-14
You're awesome dude works great!

---

