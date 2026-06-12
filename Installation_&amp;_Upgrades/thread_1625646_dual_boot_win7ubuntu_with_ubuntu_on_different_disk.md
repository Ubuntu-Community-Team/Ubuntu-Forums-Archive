---
title: "dual boot win7/ubuntu with ubuntu on different disk?"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by shaunconn on 2010-11-19
Hi

I have windows 7 installed on Disk2 (according to windows Disk Manager), and I installed ubuntu 10.10 on Disk0, choosing the dual boot option at installation.

However, grub does not load (presumably because its on disk0 and my machine appears to boot from disk3), so the machine goes straight into windows 7.

How do I get ubuntu to load?

Shaun

---

### Post by dino99 on 2010-11-19
into the bios, set your hdd where ubuntu is installed to "first choice" to boot as you have several hdds

boot on ubuntu then :

sudo grub-mkconfig
sudo update-grub

---

### Post by shaunconn on 2010-11-19
Brilliant!  Thank you, that worked perfectly.

Shaun

---

