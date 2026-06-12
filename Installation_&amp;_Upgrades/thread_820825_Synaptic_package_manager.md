---
title: "Synaptic package manager"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by thunderboltz on 2008-06-06
Hello

I'd like to know if the synaptic package manager saves a copy of the installation/source file of all the downloads that it has completed.

If yes, then I'd like to know where they are stored, and if it is fine to delete them in order to save space.

TIA!

---

### Post by briandu on 2008-06-06
open xterm and enter:

sudo apt-get clean

this will clear out much junk

also yo do not need to clear out this is not Windoze

---

### Post by dje on 2008-06-06
It is safe to delete them just run this in a terminal:
```
sudo apt-get clean
```
They are stored in /var/cache/apt, running the above automatically deletes them from that directory

hope that helps,
dje

---

### Post by thunderboltz on 2008-06-07
Thanks! I needed this as I'm on a system with limited memory.

---

