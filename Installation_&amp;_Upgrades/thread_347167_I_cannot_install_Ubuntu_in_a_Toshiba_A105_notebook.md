---
title: "I cannot install Ubuntu in a Toshiba A105 notebook!!!!"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by hsalgado on 2007-01-26
Hi Friends, I am new to Ubuntu and to this forum.  I tried to install ubuntu in my Toshiba A105, but I can not resize the HD partition.  I have tried partition magic and the Ubuntu installation program but I have not been able to do it.  It seems that the system includes an additional partition in the HD, which windows can not read, where it store files to make the media express to work (for watching movies and listening cds without having to start windows).  I guess that is the source of problem, but I am not sure, and I don´t know how to solve it.  The system has a SATA HD with 120Gb.  Any help would be greatly appreciated.  I hope I can make the change from Windows to Ubuntu smooth... so far I have not even been able to install Ubuntu!

Thanks for any help.

---

### Post by logos34 on 2007-01-26
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by Skidpad on 2007-01-26
> **logos34 said:**
> [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
^^ Great info there.  I installed Edgy on my laptop a few weeks ago after having problems resizing the partition.   The pagefile & hibernation file wouldn't let me resize. I followed the guide, and viola! Edgy installed!

If this is indeed your problem (once you eliminate those files), Gparted should allow you to install Ubuntu and not disturb the media express partition.  Make sure you've backed up everything first!

Let us know how you make out with it.

---

### Post by hsalgado on 2007-01-27
> **Skidpad said:**
> ^^ The pagefile & hibernation file wouldn't let me resize. I followed the guide, and viola! Edgy installed!
Let us know how you make out with it.

That was exactly my problem!!!  I followed the instructions about how to uninstall the pagefile and hibernation files and everything worked perfectly!  Finally, I will start enjoying Ubuntu...:guitar: 

Thanks a lot!!!!

---

