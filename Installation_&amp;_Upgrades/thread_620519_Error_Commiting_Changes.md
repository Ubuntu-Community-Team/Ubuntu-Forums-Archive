---
title: "Error Commiting Changes"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by Auax on 2007-11-22
Every time I try to upgrade/install anything through Adept, I get an Error Commiting Changes dialog. This is a brand new installation of Gutsy.

---

### Post by taurus on 2007-11-22
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by valros on 2007-12-27
i have the same problem, for both commands it says to manually run "dpkg --configure -a" to correct it. But when I run that command in the terminal it says i need superuser privileges.

I also received the cannot commit changes error when updating the mp3 codecs for amarok.

And why do the mouse buttons freeze up and give me an error sign as a cursor when i try to download realtek audio drivers from a mirror.

---

### Post by taurus on 2007-12-27
> **valros said:**
> i have the same problem, for both commands it says to manually run "dpkg --configure -a" to corrent it. But when I run that command in the terminal it says i need superuser privileges.

I also received the cannot commit changes error when updating the mp3 codecs for amarok.

Try

```
**sudo** dpkg --configure -a
sudo apt-get update
```

If you want codecs, run

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mikerduffy on 2007-12-27
> **taurus said:**
> What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

I was having this problem, so I followed your advice and typed *sudo aptitude update*.
At the end of the checks, it told me to run *sudo dpkg --configure -a*.

This new command told me that there was more than one version of a package - an installed version and the maintainer's version.  I chose the maintainer's version by typing "y", and that fixed the problem.

---

