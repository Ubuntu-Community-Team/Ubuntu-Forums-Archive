---
title: "Grub problem."
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by P2000camaro on 2010-06-23
I am currently triple booting between Windows, Mac, and Ubuntu. I was having problems booting earlier and somehow Grub2 got replaced by Grub 1.5 command line. I can't boot into Ubuntu anymore, I can only boot into a LiveCD, but I can't figure out how to re-install Grub2.. I tried using Terminal to install Grub, but it still did 1.5 command line. I did sudo apt-install grub and everything. Nothing worked.. Any suggestions??

---

### Post by darkod on 2010-06-23
Did you use grub2 on the MBR or on the ubuntu partition and chainload to it from the OSX bootloader? Which one is your ubuntu partition?

If grub1 just got on the MBR, no big deal. But if it somehow installed into ubuntu also, it might be an issue because having a grub1/grub2 mix is the worst.

---

