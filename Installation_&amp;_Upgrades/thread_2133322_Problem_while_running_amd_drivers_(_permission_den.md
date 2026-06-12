---
title: "Problem while running amd drivers ( permission denied even on root )"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by horagino12 on 2013-04-07
Hello i got back to my ubuntu since my windows has broke and its night so i cant be bothered to fix it so i went on it and i rembered that my gpu was still over heating and i didnt get any help since i had intel/amd grapichs so i went on and talked to my friend and i said the drivers are .run so he told me to open it in terminal so i went on terminal and typed this in : /home/coders/Pulpit/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run start
okay but then i saw this : /home/coders/Pulpit/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run: Permission denied
so i was like i need more rights to do this so i went on root ( sudo -i ) and i successful went on root but then i still got permission denied:
root@ubuntu:~# /home/coders/Pulpit/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run start
-su: /home/coders/Pulpit/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run: Permission denied

so can anybody help me try to install those drivers before my gpu melts?

---

### Post by MAFoElffen on 2013-04-08
That's because the script file is not set as executable yet when you first download it... Also, there are flags you need to add after the filename. Look at step #6 of my instructions:
[http://ubuntuforums.org/showthread.php?t=1743535&p=10950714#post10950714](http://ubuntuforums.org/showthread.php?t=1743535&p=10950714#post10950714)

---

### Post by Mark Phelps on 2013-04-08
If you really DO have hybrid graphics, those drivers will NOT help -- as AMD does not make hybrid graphics drivers available through their website.  Those ONLY come from the machine provider, and ONLY are available for MS Windows.  There are no hybrid graphics drivers available for download for Linux.  If you FORCE the installation of those drivers, you will only trash your display -- and then have the nightmare of having to remove them.

Hybrid graphics does NOT work well in Linux -- read the details:

[https://wiki.archlinux.org/index.php/Hybrid_graphics]("https://wiki.archlinux.org/index.php/Hybrid_graphics")

---

