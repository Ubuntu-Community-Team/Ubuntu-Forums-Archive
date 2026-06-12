---
title: "GRUB won't run after windows 10 upgrade"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by Kareem_Daker on 2015-03-27
I have a dual boot system with ubuntu 14.10 and windows 7. I recently updated windows 7 to 10 technical preview (build 10041). At first, every time I restarted the computer would go into grub rescue mode. I tried fixing reboot using the ubuntu live cd, it didn't fix it and produced this report [COLOR=#000000][FONT=Helvetica]http://paste.ubuntu.com/10681307

After that I fixed the boot issue using a windows DVD. But now it only boots into windows obviously. I ran the the boot repair again from the ubuntu live cd ([/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]http://paste.ubuntu.com/10690323) and it still boots into windows.

Has anyone installed windows 10 along side ubuntu? How can I fix grub?[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-03-27
Perhaps this is the reason

> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

No Ubuntu = no Grub. sda4 is an extended partition and inside sda4 is sda5 which is a Linux swap partition. Which partition is Ubuntu supposed to be in?

Regards.

---

### Post by oldfred on 2015-03-27
You have a large gap in you extended partition where your Linux partition was.
Windows does not see Linux partitions and rewrites partition table without it.

You should be able to use testdisk, it is in repository so you can use the Ubuntu installer in live mode and install testdisk.

You should be able to find the Linux partition and restore it. Not sure if you also have to tick every existing partition so it keeps those or not. But you want to make sure you keep those.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Similar issue, but also bad structure issue.
[http://ubuntuforums.org/showthread.php?t=2271036](http://ubuntuforums.org/showthread.php?t=2271036)

---

