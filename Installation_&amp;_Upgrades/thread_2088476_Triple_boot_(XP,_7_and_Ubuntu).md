---
title: "Triple boot (XP, 7 and Ubuntu)"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by bzykubd on 2012-11-26
Hey, 
i have a problem with my Windows systems.
I've installed 7, then Ubuntu, and after all XP.

It seems that XP installation installed bootsector on sda1, but itself is installed on sda5. At the beggining, Win 7 didnt work, but after resuce - works again. But now XP doesnt work ;p

I were trying to recover systems with boot-repair, but with no results.

Here you have log from boot-repair:
[http://paste.ubuntu.com/1389954/](http://paste.ubuntu.com/1389954/)

Do you know how to fix that wonder XP :) ?

---

### Post by oldfred on 2012-11-26
How did you install XP? It says it sector starts at sector 63 like a new install to sda1.
  
Your sda5
>     Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
Your XP install's boot.ini says it is in sda4.
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR=Red]partition(4)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(4[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```Windows always installs its boot files to the active partition. Active partition in Windows is the boot flag. Windows only boots from primary NTFS partitions, so always better to install Windows to primary partitions.

       To understand Windows booting:
To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You may be able to move boot files for XP to your XP install. Run chkdsk on sda5 to repair PBR - partition boot sector, and edit boot.ini.

Better to have XP in a primary partition.

 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

### Post by bzykubd on 2012-11-26
> **oldfred said:**
> 
How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)


Yeah! I've got it worked.
Thank you (thank you also for links to docs, very nice explained how it works).

---

