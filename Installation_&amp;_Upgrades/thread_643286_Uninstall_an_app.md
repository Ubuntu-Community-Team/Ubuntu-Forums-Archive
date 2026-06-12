---
title: "Uninstall an app?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Cygoku on 2007-12-17
1) How do I uninstall an app that I have installed using a *.deb?

1) How do I uninstall an app that I have install using Terminal with a command line such as "sudo sh something.xxx" (xxx coulbd *.run, *.rpm, *.tar.gz2, etc,...)?

Cygoku

---

### Post by LuisAugusto on 2007-12-17
> **Cygoku said:**
> 1) How do I uninstall an app that I have installed using a *.deb?

1) How do I uninstall an app that I have install using Terminal with a command line such as "sudo sh something.xxx" (xxx coulbd *.run, *.rpm, *.tar.gz2, etc,...)?

Cygoku

a) Same as the installed from repos apps, trough Synaptic.

b) It depends more, the sh could execute a lot of things. Things you compile by yourself are uninstalled the same way you compiled it (tar.gz2), with uninstall command inside the folder with the source, rpm aren't compatible with ubuntu unless you use alien, in which case, you would uninstall trough Synaptic too, the applications install by .run (usually drivers) are uninstall in the same way they were installed, running the .run.

---

### Post by chris4585 on 2007-12-17
go to System > Administration > Synaptic and search for the program you installed through the terminal or any other way, it should be listed, maybe not, but you can uninstall it from Synapic

---

### Post by Seisen on 2007-12-17
You can also remove packages from the terminal by typing in this command

```
sudo apt-get remove packagename
```

---

