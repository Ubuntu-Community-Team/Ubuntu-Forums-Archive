---
title: "I never complied in *nix sucesfuly..."
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by confy on 2007-12-13
Hello everybody. This is my first post on ubuntu forums. 
First of all i must say that i'm familiar with *nix few years and till today i never succesfuly complied anything.

This time i can't compile wireshark. I have problem with GDK+. This is what line interface says when i type ./configure

```


checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK+ isn't available, so Wireshark can't be compiled

```

however i did install essential via GUI. Any suggestions?

---

### Post by Sef on 2007-12-13
> however i did install essential via GUI.

Do you mean build essential?

---

### Post by confy on 2007-12-13
Yeah... i mean Build-essential 11.1...
i did install it from Synaptic Package Manager...

---

### Post by Partyboi2 on 2007-12-13
I believe,you need to have development files for the GTK+ and GLib libraries. 
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev
```
then try again

---

### Post by confy on 2007-12-17
yeah it worked! Thank you! :)

---

