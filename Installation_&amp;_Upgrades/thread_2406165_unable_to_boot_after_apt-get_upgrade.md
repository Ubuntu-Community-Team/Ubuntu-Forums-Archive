---
title: "unable to boot after apt-get upgrade"
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by Jeffrey_Becker on 2018-11-16
[http://paste.ubuntu.com/p/CVqHV2c8x9/](http://paste.ubuntu.com/p/CVqHV2c8x9/)

I've tried using boot repair disk and I think it's this windows partition.
None of these disks should be NTFS..
However my father said that he was able to boot to windows from Grub.. I'm so confused

UUUUGH why does every upgrade get botched for me :(
Also, this: 
[COLOR=#000000][FONT=Verdana][TABLE="class: pastetable"]
[TR]
[TD="class: code"][COLOR=#000000]The boot files of [COLOR=#666666][[/COLOR]Ubuntu 16.04.5 LTS[COLOR=#666666]][/COLOR] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition [COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. This can be performed via tools such as gParted. Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. [COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[COLOR=#666666])[/COLOR]
[/COLOR]
[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]

---

### Post by Jeffrey_Becker on 2018-11-18
Alright I've reformatted the disk it only has an ext4 partition now. I reinstalled 16.04 LTS and now my backup will not restore. 
It keeps locking up. I'm using the default backup app (deja dup). I've tried doing it from liveCD and I had to install some dependencies. It still failed.
I need to restore these backups. They have my sql databases in them for my websites.

---

