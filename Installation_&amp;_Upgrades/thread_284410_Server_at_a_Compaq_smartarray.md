---
title: "Server at a Compaq smartarray"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by zyberzero on 2006-10-25
Hi!

I got one of the Compaq DL360 servers, with the smartarray controller.
Installing Ubuntu 6.06 (and 6.10-RC) worked like a charm, but after the reboot i get the message: "cpqarray:" and something.
I've googled it and i found some solves. But the all involved to boot from the rescue mode at the CD. That step doesnt work quite well. I added eisa=0x6000 at the bootline and the resquesystem started. But i can't mount my devices (mount /dev/ida/c0d0 i think it is). My server just hangs where it is. I´ve tried using KNOPPIX 3.8 (With the 2.4 kernel) and Knoppix 4 and 5 (2.6 kernel). When i mount it, my computer says something about EFS and then just hangs.
Any suggestions?
Many thanks!

---

### Post by zyberzero on 2006-10-27
I solved it after some hours. I'll write a howto at the ubuntu-wiki soon.
/Zyber

---

