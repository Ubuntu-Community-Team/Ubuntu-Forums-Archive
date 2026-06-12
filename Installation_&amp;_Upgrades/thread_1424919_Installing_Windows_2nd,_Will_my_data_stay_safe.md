---
title: "Installing Windows 2nd, Will my data stay safe?"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Piggah on 2010-03-08
Hi, it was kinda hard to sum up my question in the title. 
What I'm asking though is: 
I have a 200GB partition where I keep my music, movies, photography, /home backups, and other really important things to make changing linux distros easier. 

I'm planning on installing 10.04 when it comes out and figure ill do a clean install. I need to install Windows XP for business purposes, and was wondering if I create an NTFS partition in gparted beforehand, will windows simply install to that partition and leave my 200GB data partition alone? (10.04 will be installed afterwards, but i know how not to overwrite when installing that.)

hope that makes sense, thanks for your time.

---

### Post by zvacet on 2010-03-09
If you create NTFS partition Windows will be installed there(you will see partition options and you will choose NTFS for Windows install).After that you will have to reinstall grub following [this]("https://help.ubuntu.com/community/Grub2") instructions.

---

