---
title: "Install lubuntu with wubi, It's easy!!"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by chinakook on 2011-11-25
An easy way to install lubuntu linux on windows and it's very simple:
 
replace the temporary installation file X:\ubuntu\install\installation.iso with lubuntu installation iso after the wubi.exe for ubuntu is executed and before the wubi prompt to restart.
 
1. download both ubuntu and lubuntu iso files, my files are ubuntu-11.10-desktop-amd64.iso and lubuntu-11.10-desktop-amd64.iso
2. extract the wubi.exe from lubuntu(or ubuntu) iso file to a same folder with the ubuntu iso file
3. execute wubi.exe, then config the installation(my target drive is D:) and click next to wait for the installation to be finished. after the wubi prompt reboot, choose manully restart.
4. replace D:\ubuntu\install\boot\initrd.lz with initrd.lz in casper dir in the lubuntu-11.10-desktop-amd64.iso file 
5. rename lubuntu-11.10-desktop-amd64.iso to installation.iso, then copy it to D:\ubuntu\install\installation.iso
Finally restart your machine to complete the installation of lubuntu
Good Luck!

---

### Post by ventsislav_nurkov on 2011-12-24
Hey, thanks a bunch for this guide!! Worked like a charm ;)

---

### Post by Zarnaik on 2012-03-10
Just what I was looking for, thanks a lot!

---

### Post by bcbc on 2012-03-10
+1 - thanks for the tip. 

Also, note that when 12.04 is released, wubi will fully support lubuntu.

---

