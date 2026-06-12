---
title: "offline synaptic installation"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by appelpeer on 2007-02-06
I have

1 computer with ubuntu OS and no internet connection
1 computer with windows xp OS and an internet connection
1 memory stick with 1Gb mem
and some empty cd-roms

and I have to install linux-header and linux-source files for my internetconnection  on my ubuntu computer who are normally obtained through synaptic.
is there a way to do this?

---

### Post by taurus on 2007-02-06
You can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) and transfer them to your Ubuntu.  Then, install them with

```
sudo dpkg -i *.deb
```

---

