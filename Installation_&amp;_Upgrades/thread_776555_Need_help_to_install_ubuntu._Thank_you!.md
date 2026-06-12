---
title: "Need help to install ubuntu. Thank you!"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Mr.Ice on 2008-04-30
Hello,
      I've been using the 7.10 and now the 8.04 Live CD for quite some time, but always afraid to install it. Ive attempted it before, but I got as far as the partioning. I have a Dell XPS M140 (Laptop) with Windows XP Media Edition preinstalled on it. It has a 90 GB HDD. Ive already partioned it, 70.6 GB for Windows and a 22.9GB (Yes, I set it to ext3 filesystem) partion for Ubuntu. But I cannot add a swap partion (I need this right?) because I already have 4 Primary partions :S. And Im afraid to make the 22.9 partion an Extended partion for some reason. So these are my questions, what partions do i need (for a laptop)? What do I make these partions (Extended Partion, Primary Partion, etc...) ? Please, Help me ive been trying for weeks (literally). Thank You!

---

### Post by peterff on 2008-04-30
I've not done it myself, but it seems that other people have successfully installed Ubuntu to an extended partition. My partition scheme is as follows:
/dev/sda1: primary partition containing Ubuntu
/dev/sda2: primary partition containing Vista
/dev/sda5: extended partition containing swap

---

### Post by Mr.Ice on 2008-04-30
Hi! 
Thanks for the reply. But I've already played around and tried to make it work, and it did! Thank you anyways!

---

