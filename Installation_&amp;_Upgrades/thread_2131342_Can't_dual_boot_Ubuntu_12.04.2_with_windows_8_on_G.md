---
title: "Can't dual boot Ubuntu 12.04.2 with windows 8 on Grub"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by hfq on 2013-04-01
Hi,

I'm trying to install dual boot (Windows 8 and Ubuntu 12.04.2) using UEFI. Followed the instructions on [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode), but the only way to get both Ubuntu and Windows working is modifying the boot option Priority in the Aptio Setup Utility.

If the Boot Option Priority is ubuntu (the other option would be Windows Boot Manager, that goes straight to windows 8), the computer goes to grub, and ubuntu the SO starts without problem. If the windows loader option is selected, the following error occurs:

ERROR: unknown command "DRIVEMAP'
ERROR: Invalid EFI filepath

this error was also occuring also before i ran the Boot-Repair api.

this is my Boot-Repair output:
[http://paste.ubuntu.com/5667865/](http://paste.ubuntu.com/5667865/)

---

### Post by oldfred on 2013-04-01
Grub2's os-prober has a bug. And normally Boot-Repair adds corrected entries into 25_custom, but I do not see them???

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Both bug report and this thread have examples, it you have to add an entry manually:
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

