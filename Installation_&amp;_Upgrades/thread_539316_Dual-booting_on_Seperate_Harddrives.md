---
title: "Dual-booting on Seperate Harddrives"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Mitch72 on 2007-08-31
Hey everyone, ubuntu newbie here :) Have to apologise if this has already been asked, but I want to install ubuntu on my secondary hard drive...

I have two hard drives- one's a 320GB SATA harddrive, which has all my windows stuff on it, and the other is a 20GB IDE harddrive, which has been connected as a master, with a DVD burner running in slave.

I want to install ubuntu on the IDE drive, and be able to dual boot into windows/ubuntu on startup.

Is there any guides/info etc about this? :confused: any help would be appreciated :)

EDIT: just found this: 
[http://wubi-installer.org/index.php]("http://wubi-installer.org/index.php") 
would this program work?

---

### Post by Pumalite on 2007-08-31
[http://www.linuxquestions.org/questions/showthread.php?t=339444](http://www.linuxquestions.org/questions/showthread.php?t=339444)

[http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

[http://ubuntuforums.org/archive/index.php/t-210595.html](http://ubuntuforums.org/archive/index.php/t-210595.html)

[http://www.linuxforums.org/forum/ubuntu-help/87393-help-dual-boot-dual-sata-ubuntu-winxp.html](http://www.linuxforums.org/forum/ubuntu-help/87393-help-dual-boot-dual-sata-ubuntu-winxp.html)

[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

[http://www.dslreports.com/forum/r18912895-dual-boot-windows-and-linux](http://www.dslreports.com/forum/r18912895-dual-boot-windows-and-linux)

[http://www.linuxcompatible.org/Dual_Boot_xp_on_sata_masterfedora_5_on_ide_master_t34945.html](http://www.linuxcompatible.org/Dual_Boot_xp_on_sata_masterfedora_5_on_ide_master_t34945.html)

---

### Post by Mitch72 on 2007-08-31
lol my bad, didn't realise there was so much stuff on it... anyway- safest way would be to...

-Unplug SATA drive, Install Ubuntu on IDE
-Set primary boot drive to IDE in bios
-Change grub menu file to enable windows option
-Plug SATA drive back in

and that would give me the option of booting into Ubuntu on the IDE and windows on the SATA on the bootloader, right?

---

### Post by Pumalite on 2007-08-31
Just about it.

---

### Post by rsambuca on 2007-08-31
I don't see why you would remove the SATA drive though.

---

### Post by Mitch72 on 2007-09-01
> **rsambuca said:**
> I don't see why you would remove the SATA drive though.

Yeah, i just remember seeing that somewhere on a forum... can't remember where though- i suppose it just makes sure there is no chance that it's touched by the install...

---

