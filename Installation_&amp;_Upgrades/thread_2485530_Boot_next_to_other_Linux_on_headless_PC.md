---
title: "Boot next to other Linux on headless PC"
date: 2023-04-01
forum: Installation &amp; Upgrades
---

### Post by wiredcharlie on 2023-04-01
I have a **headless** music server running Lubuntu 16 and in order move to Lubuntu 22 I created a second partition and did a fresh install there. 

I wish to be able to reboot from one installation to the other (both ways) whilst I configure Lubuntu 22.

efibootmgr offers a boot next feature which is perfect for this _**HEADLESS**_ situation - but it does not work.

Help appreciated

Tony

---

### Post by wiredcharlie on 2023-04-02
sudo grub-reboot 1
reboot

...allows reboot from the new installation to the old one, but does not have effect when booted to the old installation.

---

### Post by MAFoElffen on 2023-04-02
Was OS Prober 'enabled' in /etc/default/grub, when you updated grub?

---

