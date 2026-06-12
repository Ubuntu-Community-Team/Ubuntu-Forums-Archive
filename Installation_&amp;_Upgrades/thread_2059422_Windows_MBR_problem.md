---
title: "Windows MBR problem"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by aljohnston112 on 2012-09-17
I downloaded ubuntu to run in a seperate partition from windows, and I can't get windows to run anymore. I'm guessing it's an mbr problem, but I'm kind of a noob. Here's the link I got from boot-repair. 

[http://paste.ubuntu.com/1212271/](http://paste.ubuntu.com/1212271/)

---

### Post by DeezyFaReal on 2012-09-18
Do you have the Installation disk for WIndows or a system repair disk?
If you do boot from it, from the menu make sure your version of windows is not selected, select command prompt from "repair tools."
From there you need to fix mbr.
Which version of WIndows are you running?

---

### Post by DeezyFaReal on 2012-09-18
I see you're running WIndows 7
If you manage to get to the repair tools from the windows 7 disk you booted from
type this
```
bootrec.exe /FIXBOOT
```
and
```
bootrec.exe /FIXMBR
```

---

### Post by DeezyFaReal on 2012-09-18
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://help.ubuntu.com/community/DualBoot/WindowsFirst](https://help.ubuntu.com/community/DualBoot/WindowsFirst)
[https://help.ubuntu.com/community/WindowsRecoveryCd](https://help.ubuntu.com/community/WindowsRecoveryCd)

In case you don't have a recovery CD
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by darkod on 2012-09-18
In the results of bootinfo you can see that you have grub2 installed onto the win7 partition, sda1. I don't know how it got there, but it shouldn't be there.

If you have a win7 dvd or win7 rescue cd, you can do the bootrec /fixboot suggested above. Don't do the /fixmbr since that will delete grub2 on the MBR and windows bootloader can't boot ubuntu, so you don't need that.

Alternatively, if you don't have any win7 media, you can use testdisk to repair the partition boot sector. Post back if you need instructions about that.

Does ubuntu boot correctly? The results are a bit strange, they say grub2 is looking at partition #72 which doesn't make sense.

---

### Post by aljohnston112 on 2012-09-18
Not sure where the 74th partition came in when I only have 4. I used boot repair and that's what it gave me. and is the repair disk the only way to get in and fix the mbr? I don't have a disk.

---

### Post by darkod on 2012-09-18
You don't need to fix the MBR exactly. Well, maybe you do if grub2 is not working properly.

But the first thing to fix is the partition boot record (not MASTER boot record) of the win7 partition because there is a grub2 installation there and windows can't work like that.

If you don't have any windows media, boot ubuntu, download testdisk, and use it to write a Backup BS (boot sector) to partition /dev/sda1.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Note that you need to do ONLY the ntfs boot sector recovery!

---

### Post by YannBuntu on 2012-09-18
Similar tutorial for fixing the bootsector of your sda1 partition: [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by DeezyFaReal on 2012-09-19
> **darkod said:**
> If you have a win7 dvd or win7 rescue cd, you can do the bootrec /fixboot suggested above. Don't do the /fixmbr since that will delete grub2 on the MBR and windows bootloader can't boot ubuntu, so you don't need that.

That's true. My bad
When I last did the bootrec.exe /FIXMBR command, I got windows back but It made is so I could not boot into linux, and had to use Ubuntu Boot Repair.

---

### Post by DeezyFaReal on 2012-09-19
"The message you have entered is too short. Please lengthen your message to at least 1 characters."
I don't know how to delete this comment
nevermind

---

