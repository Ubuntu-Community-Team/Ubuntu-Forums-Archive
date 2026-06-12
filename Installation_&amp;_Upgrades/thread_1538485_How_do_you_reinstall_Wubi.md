---
title: "How do you reinstall Wubi?"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by mchambers25 on 2010-07-25
I have windows xp and I downloaded ubuntu 9.04 through wubi. I have recently unistalled it through the add/ remove application on windows xp and would like to know how to reinstall. I still have the dual boot option when i start my computer so i want to know the right way of reinstalling it so that i dont have another option again in the dual boot. Also i want to reinstall it to the newer version (ubuntu netbook remix for my netbook). 
 
All help would be much appreciated! Thank you

---

### Post by bcbc on 2010-07-25
sometimes the uninstall fails to remove the entry from c:\boot.ini which is why you still see the boot menu. You can edit it yourself (change it from readonly, open in notepad, delete last line with wubi/ubuntu entry) or just reinstall (I don't think it will add two entries).

You can install the ubuntu netbook edition using [wubi]("http://wubi-installer.org/"). I don't think it's called remix anymore (but I could be wrong). Wubi will download the .iso for you, but I recommend downloading it [yourself]("http://www.ubuntu.com/netbook/get-ubuntu"). Then you can easily create a bootable USB stick (either after installing wubi, or before) - it's useful as a recovery tool.  

Just place wubi.exe and the .iso in the same directory, and make sure when you run wubi you select Ubuntu Netbook from the dropdown (if you leave it as Ubuntu it will download the standard ubuntu .iso).

---

