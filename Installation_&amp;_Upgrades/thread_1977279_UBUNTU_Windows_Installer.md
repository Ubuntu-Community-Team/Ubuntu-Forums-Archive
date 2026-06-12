---
title: "UBUNTU Windows Installer"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by manirajxp on 2012-05-09
I have downloaded Ubuntu Windows Installer of size 2.38Mb WUBI.EXE when i try install it its installing but its not downloading the os iso file instead it just installs and ask me reboot but when do so no os is installed i am just directly booting in to windows os its not showing the UBUNTU os in the booting screen. Please help

Note : The Total Installation time it take is about only few minutes (2 minutes).

---

### Post by jadtech on 2012-05-09
yeah thats not right  the wubi down load is about 750mb after you got the down loader ..

---

### Post by jadtech on 2012-05-09
you can install wubi  from Live cd too   wubi windows installer only has version 11.10 the 12.04 no longer supports anything but CD or USB install ..

---

### Post by bcbc on 2012-05-09
When you run wubi.exe standalone it will download a ~500MB preinstalled compressed disk image (not the ISO). That's if you install Ubuntu. If you choose the other flavours (kubuntu/xubuntu/mythbuntu/lubuntu/edubuntu) it will download the ISO ~700MB (~2.5GB for edubuntu).

Either way, it's not going to take 2 minutes. So best if you post the logfile. You can find it in the %TEMP% directory, and it's called wubi-12.04-rev266.log. Just paste the contents between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

---

