---
title: "External CD Install..."
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Miakehl on 2006-08-25
For some strange reason when I decided to re install Ubuntu on my laptop, My DVD-RW drive also decided to break =\. I was wondering if I get an external cd-dvd burner drive and try to install to the HDD with that if I would be able to find someway to boot from that cd drive to install on the internal HDD. Also, I was wondering if there was any way to install Ubuntu without the use of a cd or floppy drive in the event I can't. 

Manythanks.

---

### Post by confused57 on 2006-08-25
Maybe this would work:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by cantormath on 2006-08-25
> **Miakehl said:**
> For some strange reason when I decided to re install Ubuntu on my laptop, My DVD-RW drive also decided to break =\. I was wondering if I get an external cd-dvd burner drive and try to install to the HDD with that if I would be able to find someway to boot from that cd drive to install on the internal HDD. Also, I was wondering if there was any way to install Ubuntu without the use of a cd or floppy drive in the event I can't. 

Manythanks.

I have installed from an external cd rom, plugin cdrom, change boot order to cd rom drive or external drive, and boot to cd .  If you dont want to use the cd, you can boot from a usb key chain, which can be alittle complicated, you could use netboot, or  tftp boot...over a network.  Alot of new bios have settings for checking for available network drives on boot.  Those are just some of the ideas I can think of.  Good luck.

---

### Post by Miakehl on 2006-08-29
My BIOS won't allow me to boot from the USB drive, and I don't think I can update the BIOS on my computer, I can't figure out how. I think theres a way to modify the boot.ini file to boot from sda1 from within windows..I dunno...It's a laptop.

---

### Post by hakre on 2006-08-30
yes, you can modify the boot.ini. I thought the link already supplied on top should describe that way.

anyway there is another solution for the boot incompabilities. the old system I'm currently installing linux on was not able to boot the cd, so I created a boot-floppy which contained it's own "bios" which then could boot the cd. that simple it was. maybe it's the same for USB?

Something of Help herein?:

INSTLUX
A linux from windows installer, that is, an installer that runs on Windows and installs linux.
[http://sourceforge.net/projects/instlux](http://sourceforge.net/projects/instlux)
[http://sourceforge.net/project/showfiles.php?group_id=151507&package_id=192787](http://sourceforge.net/project/showfiles.php?group_id=151507&package_id=192787)

---

