---
title: "Update Problems"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by osiris2258 on 2007-09-21
my update manager has started giving me this message when I try to check for updates:

W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57

so now I can't seem to update anything.

Anybody know what this is?

---

### Post by Pumalite on 2007-09-21
Did you recently add this: : [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) to your sources.list?
If so, you should go back to the site and get the key, or remove it from your sources.list.

---

### Post by osiris2258 on 2007-09-21
I tried using 
wget [http://debian.cafuego.net/969F3F57.gpg](http://debian.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

but  it didn't work.

---

### Post by Pumalite on 2007-09-21
Then comment out in your sources.list. Or you can visit the site and get more precise instructions in how to obtain the key.

---

### Post by osiris2258 on 2007-09-22
sources.list?

---

### Post by Pumalite on 2007-09-22
Backup first:
sudo /etc/apt/sources.list /etc/apt/sources.list.back, then
sudo gedit /etc/apt/sources.list
Comment out the entry in question. ( add# in front of it)
Save,exit, and try sudo apt-get again.

---

### Post by PmDematagoda on 2007-09-23
Hey Pumalite, I have a very slight problem, now I have Gutsy's kernel, but I have Update manager trying to tell me that the latest 2.6.20-16 kernel update is available, is it okay if I install this or is it not?

---

### Post by Pumalite on 2007-09-23
If you have Gutsy's kernel; stick with it.

---

