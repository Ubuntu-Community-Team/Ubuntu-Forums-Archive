---
title: "Trouble with Dual-Boot"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by pseudonym2 on 2017-01-16
Hello!
The other day, I installed Ubuntu on my Lenovo laptop, telling the installer to dual boot with the existing Windows 10 install. 
The GRUB menu appears, but if I choose to boot Windows, it comes up with an error saying something about not finding the windows boot manager and to press any key to exit. Windows is still there, however, as I can start Windows by manually tweaking the boot order.
Does anyone know what's going on?

Thanks.

---

### Post by oldfred on 2017-01-16
Are you then only booting Windows from UEFI boot menu?

Of Ubuntu is in UEFI boot mode.
Grub only boots working Windows. And that includes Windows that is hibernated or needs chkdsk.
And Windows 10's fast start up is always on hibernation.
Grub booted in BIOS mode will not boot any other install in UEFI boot mode.

You can continue to boot from UEFI boot menu, not grub menu. Or turn off fast start up.
The hibernation also leaves all NTFS partitions hibernated, so if you are using a shared NTFS data partition, you must turn off fast start up.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

