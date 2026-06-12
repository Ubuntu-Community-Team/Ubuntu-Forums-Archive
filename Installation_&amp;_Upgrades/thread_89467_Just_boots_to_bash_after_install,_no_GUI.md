---
title: "Just boots to bash after install, no GUI"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Pogo708 on 2005-11-12
I'm new to Linux, and I tried installing Ubuntu 5.10 i386 on a completely blank hard drive in my computer with no other OSes. Instead of booting to a desktop after I install like it says it should in the instructions, I just get a command line login. I can login, but it just stays at the command line, there's no GUI or anything. What do I do? Thanks.

---

### Post by invalid on 2005-11-12
It sounds like maybe you chose to install the "server" package by mistake maybe? Try the command
```
sudo gdm
```
and see what output you get.

Cheers,
Cb

---

### Post by Pogo708 on 2005-11-12
It recognizes the sudo command, but when I put gdm after it I just get an error.

---

### Post by invalid on 2005-11-12
What is the error, command not found? Or something else?
If you could post it here, that would lead us somewhere.

Cb

---

### Post by Pogo708 on 2005-11-12
Yeah, it's:

```
sudo: gdm: command not found
```

I'm running this as root. Should I just use my normal account?

---

### Post by invalid on 2005-11-12
Use
```
sudo apt-get install ubuntu-desktop
```
to install Gnome desktop
or
```
sudo apt-get install kubuntu-desktop
```
to install KDE enviornment.

Cheers,
Cb

---

### Post by Pogo708 on 2005-11-12
Sweet, thanks!

---

### Post by Pogo708 on 2005-11-12
Er, now what? I did that and nothing changed...

---

### Post by invalid on 2005-11-12
Now run 
```
sudo gdm
```
or restart your computer.

Cheers,
Cb

---

