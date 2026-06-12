---
title: "Minimal base/core install?"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by LinUxaliVe on 2012-03-27
Hello.

While I've already tried the net minimal installer, it pulled in way too many packages to be setting up a basic cli interface. It also took like 30-40 minutes to download the packages, and consistently failed on the "installing software" phase. 

I've also tried the full 700+ MB iso, but even it decided to "download" stuff. Even with the "download updates" unchecked, it took about 30-40 min to download "whatever it was in the background. I then spent another hour removing packages, and their dependencies, that I didn't need. In the end, I couldn't get everything as it kept trying to startx on tty7.

Could someone not necessarily help me find out "how to", but tell me "if" the following is possible?

A minimal Ubuntu install with only the core Linux components.
- Command line only with no X
- No start-up, or update, scripts
- No splash screens, or auto-login attempts

---

### Post by Bucky Ball on 2012-03-27
Which release of the mini.iso are you downloading?

---

### Post by LinUxaliVe on 2012-03-27
64-bit PC (amd64, x86_64)

[Ubuntu 11.10 "Oneiric Ocelot" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/mini.iso") 26MB (MD5: 407bf3a2b1d56af8e01aecfc6fdcbc9d, SHA1: 6eebf8cf79ae4f838ef88e43b9caa0ea1a92d2c)

Yes, I know there are other Linuxes out there that may be more suited to an install of this sort. I chose Ubuntu because of the large user base, large package repos, and the unofficial ppas.

---

### Post by Bucky Ball on 2012-03-27
> **LinUxaliVe said:**
> 

Yes, I know there are other Linuxes out there that may be more suited to an install of this sort. 

Wasn't thinking that. Just confirming it wasn't 12.04 LTS. ;)

---

### Post by 2F4U on 2012-03-27
Have you ever thought about using the Server install cd? It may be exactly what you are looking for. By default, no GUI whatsoever is installed, but you can add things as you like.

---

### Post by Bucky Ball on 2012-03-27
> **2F4U said:**
> Have you ever thought about using the Server install cd? It may be exactly what you are looking for. By default, no GUI whatsoever is installed, but you can add things as you like.

But ... it does drag in things you need for a server set-up which will be superfluous if you're not running the machine as a server and OP wants to go as stripped back as possible by the sounds of it ... ;)

---

### Post by LinUxaliVe on 2012-03-27
It isn't that I won't install a GUI at some point. It just is that I want a base system which I can then build up the way I want without having my system cluttered up with stuff. In addition to that, it'd be way easier to do the initial update, and upgrade, before installing any packages.

So I take it that there aren't distribution methods for getting a system up and running based on only what it takes to boot up to the console (at least officially)?

---

### Post by jerrrys on 2012-03-27
Both the mini.iso and the alt-install-cd will do a terminal only install.  Maybe i just don't understand.

---

### Post by LinUxaliVe on 2012-03-27
> **jerrrys said:**
> Both the mini.iso and the alt-install-cd will do a terminal only install.  Maybe i just don't understand.

No. I  was just confirming that there was a way. Now I have to find out why the net installer is crapping out. Thanks.

---

