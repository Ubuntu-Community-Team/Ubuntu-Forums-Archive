---
title: "Recommended program for multipart downloading??"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by Portable_Jim on 2006-12-13
I want to download part of a file one morning and then turn off my computer during the night. Then download more of the file the next morning and turn the computer off during the night...

Anyone recommend a program to do that? downthemall (Firefox extension) looses the progress when I turn my computer off.

(I am download the edgy ISO file)

---

### Post by happy-and-lost on 2006-12-13
sudo apt-get gwget

It's a gtk frontend to wget which can pause downloads

---

### Post by Portable_Jim on 2006-12-13
HELP:
```
 ****@jamescomputer_L:~$ apt-get gwget
E: Invalid operation gwget
```

---

### Post by taurus on 2006-12-13
```
sudo aptitude update
sudo aptitude install gwget
```

---

### Post by Portable_Jim on 2006-12-13
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install gwget
```
I just used Synaptic

---

### Post by Portable_Jim on 2006-12-13
> **Portable_Jim said:**
> I just used Synaptic
Thanks happy-and-lost and taurus

---

### Post by happy-and-lost on 2006-12-14
How long have I been using Debian based Linuxes? Sorry about forgetting the install!

---

### Post by Portable_Jim on 2006-12-15
> **happy-and-lost said:**
> How long have I been using Debian based Linuxes? Sorry about forgetting the install!
that's alright. it is working now. Thanks again

---

### Post by Portable_Jim on 2006-12-15
Now how do I stop it part way through a file?

---

### Post by Portable_Jim on 2006-12-15
(bump)

---

### Post by happy-and-lost on 2006-12-16
Right Click and select "Pause"

---

