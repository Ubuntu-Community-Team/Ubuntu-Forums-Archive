---
title: "Always getting the 'grub&gt;' line command when booting"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by eric.delarochette on 2014-01-08
Hi there,

I installed Ubuntu Studio 13.10 alongside a preinstalled Windows 8.1 (upgraded from Windows 8 before installing Ubuntu). This is on a recent (2013) TOSHIBA Satellite C870D-121 laptop that can only boot in UEFI mode.
After 3 attempts with boot-repair, all I can  is the 'grub>' command line.
The generated boot-repair reports a


[LIST]
[*][6715137]("http://paste.ubuntu.com/6715137")
[*][6715291]("http://paste.ubuntu.com/6715291")
[*][6715434]("http://paste.ubuntu.com/6715434")
[/LIST]

The GNU GRUB version is 2.00-19ubuntu2.1
Is there anything else I can try to get this issue fix?
Thanks.

---

### Post by oldfred on 2014-01-08
Some info on a slightly different Toshiba model.
 Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)

Does Windows boot?

If you can boot the Ubuntu entry from UEFI (even if not working now), do not say yes to this. It is only for system that do not let you use ubuntu entry in UEFI and are hard coded to only boot Windows.
> 

 WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? no



---

