---
title: "program for exe to open"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by steven5145 on 2008-10-19
What is a good program to dowload for opening .exe files?

---

### Post by Capt. Mac on 2008-10-19
Wine?

---

### Post by steven5145 on 2008-10-19
> **Capt. Mac said:**
> Wine?

how do i install it?

it's my first computer with ubuntu 

ubuntu is new for my

---

### Post by Partyboi2 on 2008-10-19
You can search for it in add/remove (Applications>Add/Remove) or by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install wine
```

---

### Post by steven5145 on 2008-10-19
[QUOTE=Partyboi2;5993070]You can search for it in add/remove (Applications>Add/Remove) or by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install wine
```[/

on my screen i get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

What do i gave to do?

---

### Post by Monotoko on 2008-10-19
try running
```

dpkg --configure -a

```

first :P

---

### Post by Sycron on 2008-10-19
Open up a terminal and type ```
sudo dpkg --configure -a
```.

---

### Post by stinger30au on 2008-10-19
depends what the program is, it may not run in wine



you may have to install "vitrual box" and install your copy of windows

---

