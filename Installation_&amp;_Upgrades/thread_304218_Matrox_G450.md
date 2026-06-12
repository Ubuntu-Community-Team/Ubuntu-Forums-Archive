---
title: "Matrox G450"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by robytex on 2006-11-21
Hi, I'm a rooky with linux
I've downloaded from matrox site the driver for my VGA.
Now I've this file:

matrox_driver-x86_32-4.4.0.tar.gz

Inside it there is a install.sh file.
Now....what can I do to install it?
Who could give me a simple step by step guide to do it?
TIA.

Robytex

---

### Post by daller on 2006-11-21
Goto the directory where the file is located.

Open a terminal in that location.

Run:

```
sudo sh install.sh
```

Then it should install if the dependencies are right!

Please try, and post possible errors.

---

### Post by robytex on 2006-11-21
Terrible...this is the output

ktop:~/Desktop/matrox_driver-x86_32-4.4.0$ sudo sh install.sh
[: 43: ==: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found
install.sh: 141: function: not found
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
-e \E[31mERROR: The X server drivers included in this installation package
-e        do not support the current version of your X server.

and now? what can I do? I'm new (on ubuntu) but linux is very frustating](*,)

---

### Post by daller on 2006-11-21
The driver does not support the current version of Xorg. (which is nearly impossiple to correct!)

You should look around for another driver!

This is German, but the commands are still English :D - Try it:

[http://wiki.ubuntuusers.de/Matrox](http://wiki.ubuntuusers.de/Matrox)

Do you want to get 3D acceleration, or what is your goal with installing the binary driver?

---

### Post by robytex on 2006-11-21
I want to get 3d acc, because blender dosen't start.
I will try with the link you suggested to me.
Thanks

Robytex

---

