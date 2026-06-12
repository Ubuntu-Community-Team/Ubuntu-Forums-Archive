---
title: "can not reboot after upgrade to 15.10 from 15.04 (Ubuntu)"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by hseuming on 2015-11-30
Hi,
After upgrading to 15.10 from 15.04, I can no longer boot up my computer.   I don't have multi-boot OS's configured and Ubuntu is the only OS on this computer.   The error message is as follows:

====================================================
error: unknown filesystem
Entering rescue mode ...
grub rescue>

grub rescue>   ls
(hd0) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1) (hd2)
====================================================

When i tried boot-repair as described at[INDENT][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[/INDENT]
 i ran into the following problem:
     The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.

The pastebin URL is
          [http://paste.ubuntu.com/13570843/](http://paste.ubuntu.com/13570843/)

 
All input welcome. 

Thanks for reading.

---

