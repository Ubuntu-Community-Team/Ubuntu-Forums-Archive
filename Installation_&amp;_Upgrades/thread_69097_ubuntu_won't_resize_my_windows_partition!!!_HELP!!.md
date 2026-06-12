---
title: "ubuntu won't resize my windows partition!!! HELP!!!"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by quadomatic on 2005-09-25
I followed this guide to try to resize my hard drive:[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Every time when i enter size and type in a new size or percentage for the windows partition, and hit enter, it goes back to the partition table and there is no change in the size of my partition. Why does this keep happening? I can't get qtparted on a cd cuz i dont have any cdrs left...i used my last one to burn ubuntu...How can I get Ubuntu to resize my windows partition????

PLZ HELP!!!

BTW: I'm using the 5.04 cd

---

### Post by papangul on 2005-09-25
Do you want to resize the C: drive? Is it a fat32 partition? Then you may use a program called "fips"(from windows) to resize the partition and use the free space during Ubuntu installation.

---

### Post by quadomatic on 2005-09-25
[QUOTE=papangul]Do you want to resize the C: drive? Is it a fat32 partition? Then you may use a program called "fips"(from windows) to resize the partition and use the free space during Ubuntu installation.[/QUOTE]

yeah, the c drive...its an ntfs partition with windows xp on it

---

### Post by Quirky on 2005-09-25
Have you definitely defragmented your XP partition? Even if the XP checker thing says that you don't need to, you still really do need to. If you don't, there may be files in the area you are trying to resize and the parition tool prevents you from making the change.

---

