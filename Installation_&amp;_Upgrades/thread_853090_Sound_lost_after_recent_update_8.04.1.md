---
title: "Sound lost after recent update 8.04.1"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by MrMatt on 2008-07-08
Okay.

I am running Ubuntu 8.04.1 64 Bit edition.

I installed it off a brand spanking newly burned disc just this morning.

Earlier today there were no sound issues to speak of.

However, after some updates and a restart I have lost sound.

I am using a Giga-byte GA-965P-DQ6 Motherboard with a built in Realtek AC97 ALC888 on-board sound card.

and now a new-comer has arrived in my sound manager, called "HDA Intel"

as far as I can tell, my system only can use the Intel... which in turn provides no sound for me.

Can anyone suggest how I might fix this?
or any other information I can provide (and how to provide it if needed)?

Thanks for Reading

---

### Post by Pumalite on 2008-07-08
Open up all your ports; including: proposed, partner, updates and backports:
System>Administration>Software Sources
The do:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by MrMatt on 2008-07-08
fixed thank you :)

---

### Post by Pumalite on 2008-07-08
You are welcome. Good luck!

---

