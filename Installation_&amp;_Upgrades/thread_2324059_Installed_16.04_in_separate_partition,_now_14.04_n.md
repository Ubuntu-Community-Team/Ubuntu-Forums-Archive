---
title: "Installed 16.04 in separate partition, now 14.04 not booting"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by jamarsh123 on 2016-05-10
Longtime user of Ubuntu 14.04, but I wanted to try Ubuntu 16.04, so I installed it into a separate partition. I also reinstalled the boot partition, expecting grub2 to find both versions as boot options. I tried 'update-grub'. All the OS versions are detected, but when I restart the computer, grub does not present Ubuntu 14.04 as an option.

---

### Post by oldfred on 2016-05-10
If update-grub shows it, then it should be in menu.
Or are you updating the old install and grub in MBR is now from new install.
You have to run update-grub in all installs on a new kernel. 
And only one install can control MBR (if BIOS).

You can manually reconfigure to boot a grub entry that is based on partition, not on specific kernel. Then you do not have to run update-grub all the time.

To see what grub and versions are where:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205) 

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by jamarsh123 on 2016-05-10
update-grub does show it, but it is not in the menu.
16.04 is a fresh install, including grub, in separate partition, which has replaced the previous grub. 
I ran update-grub on the new installation only.
Working on the boot-info  report now.

And here is the link to the boot-info report
[http://paste2.org/XdvKxjJ0](http://paste2.org/XdvKxjJ0)

---

### Post by jamarsh123 on 2016-05-10
Here is the link to the boot-info report
[http://paste2.org/XdvKxjJ0](http://paste2.org/XdvKxjJ0)

---

### Post by jamarsh123 on 2016-05-10
Sorry for the inconvenience, but I think I need to close this thread. I've managed to boot into my original version, 14.04. Thanks for the response.

---

### Post by oldfred on 2016-05-10
I see you have separate /boot partition.
Generally with most desktops, it is better not to have /boot as a separate partition. Some LVM or server type installs may need a separate /boot.

And never share a /boot with different installs. It will lead to conflicts.

---

