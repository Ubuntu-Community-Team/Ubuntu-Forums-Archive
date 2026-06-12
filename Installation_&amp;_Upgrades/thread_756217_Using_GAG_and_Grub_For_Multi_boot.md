---
title: "Using GAG and Grub For Multi boot"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by wolverineik on 2008-04-15
Hello everyone,

I am thinking of installing Ubuntu 7.10 on my new hard disk. I already have Windows 2000 & XP installed on my system, and am using GAG to load them up. However, I'm not sure that if I install Ubuntu, wether GRUB will ovewrite the MBR, and how I can overcome the problem.

ANy assistance would be greatly appreciated,

Irfan

---

### Post by Pumalite on 2008-04-15
You can install Grub to it's own partition. I advise you not to fear and let Grub install to your Windows MBR. You will have triple boot. We can always modify menu.lst if need be. OTOH, it's very easy to restore your Windows MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

