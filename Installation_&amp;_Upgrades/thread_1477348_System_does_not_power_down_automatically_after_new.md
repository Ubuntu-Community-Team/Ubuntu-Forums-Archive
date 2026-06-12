---
title: "System does not power down automatically after new installation"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by epp on 2010-05-08
I installed Ubuntu on a Compaq system with a 32-bit AMD Athlon CPU (i686 architecture), circa 1999.  

Because something pertaining to IDE/SCSI drivers in Linux changed during 2008, no Linux distro released since then will install from scratch on this machine and I know there was a bug filed on this problem at Launchpad.

So, I had to use Ubuntu 7.10 to do the initial installation, then upgraded it to 8.10 LTS, then a further upgrade from 8.10 to 10.04 LTS.

However, when shutting down the system, it will not power off.  A previous Linux distribution used on this, as well as Windows, both powered the system off correctly.  Is there something that I need to add to the GRUB boot parameters so it powers down and if so, which file would this be appended to (or which GUI application is used to add it)?

Currently, the only way to power it off is to hold in the power button for up to 10 seconds until it powers off.

Thanks in advance for any information.

---

### Post by epp on 2010-05-11
No one knows???  :confused:

---

### Post by wkulecz on 2010-05-11
I don't know what is going on here.  Mine is a quad core desktop and usually it powers off after shutdown but occasionally it hangs with the Ubuntu with dots below it logo showing and never powers off, system seems halded and Caps/Num lock keyboard LEDs do not toggle on the keypresses and Ctrl-Alt-DEL is ignored.

I've all power management disabled.  I don't shutdown often so its not a big deal for me though.

---

### Post by epp on 2010-05-30
Adding *reboot=warm* and *acpi=force* to the boot parameters in /boot/grub/menu.lst, solved this problem.

---

