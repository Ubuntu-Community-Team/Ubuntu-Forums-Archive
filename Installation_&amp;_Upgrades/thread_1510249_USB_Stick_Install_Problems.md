---
title: "USB Stick Install Problems"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by John_1967 on 2010-06-15
I have a question about USB Stick issues with Ubuntu 10.04. I have installed Ubuntu to a 4GB stick and it works fine but if I try to update it using the Update Manager if finds the files I need, downloads them, but half way through my install of the updated files the system reports that it has run out of space. I have a 1 GB Casper file on the stick and my download is under 300MB of compressed files. Do the file updates go to the casper file or the system side of the house. I am a little confused on this matter. I searched to see if someone else had this issue but didn't get the answer I was looking for. Thanks in advance for your help!

---

### Post by C.S.Cameron on 2010-06-15
All changes to a persistent flash drive are saved to the casper-rw file.
The kernel is frozen and can't be changed, (easily).
If you update a program you can't get rd of the previous version.
If you want to be able to update or upgrade, do a full install, just lie you are installing to an internal hard drive.
I would suggest unplugging your internal drive first.

---

### Post by John_1967 on 2010-06-15
Thank you very much for the info and help!

---

