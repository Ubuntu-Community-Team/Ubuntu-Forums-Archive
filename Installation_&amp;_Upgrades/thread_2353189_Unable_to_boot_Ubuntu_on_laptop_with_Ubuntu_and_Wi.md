---
title: "Unable to boot Ubuntu on laptop with Ubuntu and Win 10"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by pesilat-2000 on 2017-02-19
Hello,
  Currently when I boot up I can only choose Win 10.  If I want to use Ubuntu I have to boot from a USB drive.   Once I boot from the USB I can use Ubuntu with the USB inserted.  It saves my files, favorites, etc.  i ran boot -info and got this output [http://paste2.org/vKPPVZhf](http://paste2.org/vKPPVZhf)     Any help greatly appreciated as I would like to choose booting Win 10 or Unbuntu without relying on the flash drive.

Thanks,
Travis

---

### Post by oldfred on 2017-02-19
How you boot install media UEFI or BIOS is then how it installs.

You have Windows installed in UEFI boot mode on gpt partitioned drive.
But you tried to install Ubuntu in BIOS mode on gpt drive without the required bios_grub partition. If you really want Ubuntu in BIOS boot mode, add a tiny 1 or 2MB unformatted partition and add the bios_grub flag. Then use Boot-Repair in BIOS mode to reinstall grub to MBR.

But UEFI & BIOS are not really compatible. You can only boot from UEFI.
And once started to boot or at grub menu, can only boot other installs in same boot mode as grub is installed. So if booted in BIOS mode you could boot other installs in BIOS mode, but not your Windows UEFI install.

Better to boot Ubuntu installer in UEFI mode, and use Boot-Repair's advanced mode to totally uninstall grub and reinstall it. That will remove BIOS version of grub and install the UEFI version. Then you can dual boot Windows as long as Windows works. But Windows cannot be hibernated nor need chkdsk. And Windows updates will probably turn fast start up or always on hibernation back on. Then you can only directly boot Windows from UEFI boot menu to turn it off again.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

