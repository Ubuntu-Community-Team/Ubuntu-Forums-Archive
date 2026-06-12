---
title: "Tried to install Ubuntu, now computer won't boot, HELP!"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by colo3 on 2014-10-08
Hi,

I have  a new Acer Aspire S7. I tried to install Ubuntu, alongside Windows 8, but i messed up in the middle, and now i can't even run Windows 8. I'm desperated, when i turn the computer on, it asks me to enter a bootable device. I made a backup with the Acer tool, but it doesn't seem to work. I don't know what to do, please help me!

I leave you the report of what boot-repair returned: [http://paste.ubuntu.com/8520860/](http://paste.ubuntu.com/8520860/)

Thanks.

---

### Post by oldfred on 2014-10-08
Script does not show much, as it cannot mount any partitions to see what is in them. But partition table is shown and it gives this error which does not look correct.

> /dev/sda4 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
/dev/sda6 ends after the last sector of /dev/sda
/dev/sda7 ends after the last sector of /dev/sda
/dev/sda8 ends after the last sector of /dev/sda

I do not think live installer includes gdisk. 
So boot live installer in live mode and install gdisk and run it. Do not make any changes with w or write command but post what it says about drive.

       sudo apt-get install gdisk
sudo gdisk -l /dev/sda
GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Was/Is this a dual drive but RAIDed system?  I do not know much about RAID.
      
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

