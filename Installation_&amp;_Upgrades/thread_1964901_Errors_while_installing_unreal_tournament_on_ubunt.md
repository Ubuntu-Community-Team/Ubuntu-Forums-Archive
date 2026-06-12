---
title: "Errors while installing unreal tournament on ubuntu 11.10"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by Jitarth on 2012-04-24
Hi, I am trying to install my old unreal tournament on ubuntu 11.10 but am facing some errors.

[https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

My game does not install even after following the above article.

First i got this error

```
error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

then after adding few repositories i installed libgtk1.2.

Now the following error appears in the terminal with a installer with no text.

```
jitarth@jitarth-Homeame:~/Downloads$ ./ut-install.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

```

[IMG]http://s16.postimage.org/fw8jl2zh1/Screenshot_at_2012_04_25_03_33_34.png[/IMG]

---

### Post by Jitarth on 2012-04-25
Has any one else had similar problems?

My pc has the given specs:

Pentium D 2.8 ghz
1 gb DDR1 Ram
40 GB Harddisk
and inbuilt graphics processor
mother board is asus p5pe vm


could this be due to an old pc??

---

