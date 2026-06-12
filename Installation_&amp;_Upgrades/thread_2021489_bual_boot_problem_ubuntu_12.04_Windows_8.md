---
title: "bual boot problem ubuntu 12.04 Windows 8"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by disco_kiza on 2012-07-09
I have installed windows 8 on a separate hard disk and i dont see windows 8 in grub menu.

I have tried searching on forum, but my lack of linux knowledge has prevented me from solving this issue.

If somebody has a spare time to take me step by step i would i would appreciate it. 

[http://paste.ubuntu.com/1082904/](http://paste.ubuntu.com/1082904/)

---

### Post by darkod on 2012-07-09
Boot ubuntu and in terminal run:
sudo update-grub

That should pick up win8 and make an entry in the boot menu.

---

### Post by disco_kiza on 2012-07-09
Vec sam probao to i nije ga pokupio :(


Just in case here`s in english. 
I have already tried it and it did not work.

---

### Post by darkod on 2012-07-09
In that case, you are missing some of the boot files. They might have been on another partition that you deleted or formatted after the win8 installation. Windows can put them on another partition without warning.

Why is the boot flag on sda1? It should be on the win8 partition, sdb1. Use Gparted and remove the boot flag from sda1, then put a boot flag on sdb1.

After that use the win8 dvd and try the automatica repair process (you might need to run it 3-4 times to fix everything). That should boot win8 automatically. Not sure if it will put the windows bootloader on sda or sdb.

In case it overwrites your grub2 on sda, just restore it, and doing the update-grub should work once win8 has all its boot files.

---

### Post by disco_kiza on 2012-07-09
Let me try this, and ill get back at you later.

---

### Post by YannBuntu on 2012-07-10
Hello

I see no problem with the boot flag. There is one on sda1 and one on sdb1, which is ok.

```
=================== os-prober:
/dev/sda5:The OS now in use - Ubuntu 12.04 LTS CurrentSession:linux
```

Windows is not detected by os-prober, so update-grub will not help.

Is see 2 problems:

1) No BCD in sdb1:

```
sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe
```

2) Hibernation:

```
Windows is hibernated, refused to mount.
```

If I were you, I would:
1° boot on a Windows CD and use its console to repair Windows, via the following commands:
```
bootrec /FixMbr
bootrec /FixBoot
Bcdboot C:\windows
bootrec /RebuildBcd
```
2° then use Boot-Repair's Recommended repair to recover the GRUB menu.

---

### Post by disco_kiza on 2012-07-10
@YannBuntu

i have tried your advice. Boot windows from my USB and went to command line.  

bootrec /FixMbr  was ok
bootrec /FixBoot i got a massage "element not found"? so i had to stop there. 

Any more advice?

---

### Post by disco_kiza on 2012-07-10
How about if i re-install windows and then run ubuntu from live cd and run boot repair?

---

### Post by darkod on 2012-07-10
> **disco_kiza said:**
> How about if i re-install windows and then run ubuntu from live cd and run boot repair?

I would do that. And I would also remove the boot flag from sda1. Windows depends heavily on the boot flag as destination on which partition to put the boot files. So leave the boot flag only on the partition you are planning for win8, in other words sdb1.

I would also format sdb1 first, so it's clean and you don't need to do anything with the win8 installer, just tell it where to install.

---

### Post by YannBuntu on 2012-07-11
+1

Also, if you can, disconnect the Ubuntu disk before installing Windows.

---

### Post by disco_kiza on 2012-07-12
Well, i have disconnected ubuntu disk, formatted windows disk and run clean installation.

After that, i have reconnected ubuntu disk, boot live ubuntu and ran boot repair. Now i see windows in grub but when i boot windows it starts to boot and pop up an error massage for 1 sec (so cant read it) and reboot it self. 

I will try to run windows repair and see where it will take me :)

---

### Post by disco_kiza on 2012-07-13
Thanks darkod and YannBuntu, i did it. Windows repair did the job. Now i have Ubuntu 12.04 and windows 8 working.

---

### Post by YannBuntu on 2012-07-13
Good job and happy Ubuntu-ing :)

---

### Post by oldfred on 2012-07-13
If you are dual booting you may want to turn the auto hibernation off.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by hovrashko on 2012-07-13
so the problem persisted in windows, because i usually will re-install grab and it does it for me.

---

