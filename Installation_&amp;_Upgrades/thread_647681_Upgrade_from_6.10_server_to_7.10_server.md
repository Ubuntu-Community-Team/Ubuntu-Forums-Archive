---
title: "Upgrade from 6.10 server to 7.10 server"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by frodemt on 2007-12-22
Hi,

How can I upgrade from Ubuntu 6.10 server to Ubuntu 7.10 server without a GUI. I am connected through SSH.

I could not find any guide for this.

---

### Post by Pumalite on 2007-12-22
6.10>7.04>7.10

---

### Post by frodemt on 2007-12-22
> **Pumalite said:**
> 6.10>7.04>7.10

Yeah, but where to look for a guide for that?

---

### Post by Pumalite on 2007-12-22
You might want to try this:

sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade
Remember to backup everything first.

---

### Post by frodemt on 2007-12-22
Ok, Thank you.

---

### Post by Pumalite on 2007-12-22
Good Luck!

---

### Post by frodemt on 2007-12-23
It seemed to work great on the test system! I might try this on my server when I have time to backup all.

---

### Post by Pumalite on 2007-12-23
I'm glad it worked for you!

---

