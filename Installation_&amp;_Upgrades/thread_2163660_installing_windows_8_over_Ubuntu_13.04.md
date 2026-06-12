---
title: "installing windows 8 over Ubuntu 13.04"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by yichentohjoel on 2013-07-19
i have a laptop running Ubuntu 13.04 i decided to install windows 8 on it as some of my work requires it. i know that it is preferred to install Ubuntu after windows. if so should i completely replace Ubuntu and install windows 8 and then install back Ubuntu?

---

### Post by su:bhatta on 2013-07-19
you can load Window8 on your existing Ubuntu 13.04. I dont think there will be a problem. Saying from experience, I have done that.

Just remember you will not get grub on start up once Windows is installed.
That can be taken care of by a application called EasyBCD. You can use this application in your Windows8 to add Ubuntu 13.04  option at the start up screen.

These two pages gives you some idea about how to use EasyBCD:

[http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm)

[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

---

### Post by oldfred on 2013-07-19
How is system configured, UEFI or BIOS? Most are still BIOS but very new systems now use UEFI. Both Ubuntu & Windows must be the same boot mode. Windows only installs on gpt partitioned drives with UEFI or only can install with UEFI on gpt drives.

If BIOS you have the 4 primary partition limit and Windows only installs to a primary partition, formatted NTFS with the boot flag. Some format with gparted, but still have to reformat again with the Windows install disk.

---

