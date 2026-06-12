---
title: "Is Grub required for second OS?"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Kri5 on 2011-11-07
I have ubuntu already installed as my main OS but want to install and dual boot Archbang.
 
Do i need to install the grub with Archbang or can i use the grub already installed?
 
Will updating the grub in Ubuntu detect Archbang and allow me to boot it up?

---

### Post by darkod on 2011-11-07
It's up to you. I would keep using the ubuntu grub.
But for this you need to make sure you tell Arch not to install grub during the install. I don't know what the process looks like but you should be able to tell it not to install it.

On the first boot ubuntu will start as normal, it's still not aware of Arch. Just run:
sudo update-grub

and it should detect it.

---

### Post by Kri5 on 2011-11-07
Thanks darkod.
 
Archbang does give you the option not to install grub.
 
I shall give it a go and see what happens.

---

### Post by ajgreeny on 2011-11-07
You will need to run ```
sudo update-grub
``` in ubuntu to add archbang to grub and be able to boot it.

---

