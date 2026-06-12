---
title: "Grub Loading stage1.5. Error 17"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Swashy on 2009-11-20
So I have vista 32 bit and ubuntu on seperate partitions. I stopped using ubuntu a while ago and decided to uninstall delete it. After rediscovering how to delete partitions and extend old ones through a vista disk manager tool, I indeed deleted the ubuntu partition and combined it with my current vista one.

Now I'm assuming this was the absolute worst way to do this because now GRUB is stuck on it somehow, the program that lets you decide which operating system you want to start up.
How do I get rid of grub/bypass it to allow windows to start up normally?
Thanks in advance!

---

### Post by Henzor on 2009-11-20
I might know the answer even tho I'm a beginner my self. Try to disconect all your harddrives and start your computer, turn it off when you get the "no harddrive error" message. Then connect the harddrive you want as hd0 (windows drive in this case) and reboot. Have done this to fix grub error 17 and grub error 21 my self.

---

### Post by lindsay7 on 2009-11-20
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by ajgreeny on 2009-11-20
If you don't have a copy of the Windows install CD, download [Supergrub]("http://www.supergrubdisk.org/"), burn the image to a CD, and you can use that to do the same thing by booting to the CD and following the prompts to get your Windows MBR back.

I'm not sure if it works for Win7, but I think it should.

---

### Post by Swashy on 2009-11-20
Thanks for the link lindsay but it still isn't working... I ran the command fixboot, I think, and it said "operation completed successfully" in like, 3 seconds. I had trouble figuring out how to make it execute /fixboot so I'm not even sure if it did because several other variations of what I think executes fixboot also said "completed the operation successfully".

> **ajgreeny said:**
> If you don't have a copy of the Windows install CD, download [Supergrub]("http://www.supergrubdisk.org/"), burn the image to a CD, and you can use that to do the same thing by booting to the CD and following the prompts to get your Windows MBR back.

I'm not sure if it works for Win7, but I think it should.

Ummm is MBR the manual booter?

---

### Post by Swashy on 2009-11-20
Nvm, /fixMbr worked! Thanks!

---

### Post by lindsay7 on 2009-11-20
Good for you!

---

### Post by lindsay7 on 2009-11-20
For ajgreeny,

It will fix windows 7, see below.

```
Bootrec.exe options
The Bootrec.exe tool supports the following options. Use the option that is appropriate for your situation.

Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd

/FixMbr
The /FixMbr option writes a Windows 7 or Windows Vista-compatible MBR to the system partition. This option does not overwrite the existing partition table. Use this option when you must resolve MBR corruption issues, or when you have to remove non-standard code from the MBR.
/FixBoot
The /FixBoot option writes a new boot sector to the system partition by using a boot sector that is compatible with Windows Vista or Windows 7. Use this option if one of the following conditions is true:

    * The boot sector has been replaced with a non-standard Windows Vista or Windows 7 boot sector.
    * The boot sector is damaged.
    * An earlier Windows operating system has been installed after Windows Vista or Windows 7 was installed. In this scenario, the computer starts by using Windows NT Loader (NTLDR) instead of Windows Boot Manager (Bootmgr.exe).

/ScanOs
The /ScanOs option scans all disks for installations that are compatible with Windows Vista or Windows 7. Additionally, this option displays the entries that are currently not in the BCD store. Use this option when there are Windows Vista or Windows 7 installations that the Boot Manager menu does not list.
/RebuildBcd
The /RebuildBcd option scans all disks for installations that are compatible with Windows Vista or Windows 7. Additionally, this option lets you select the installations that you want to add to the BCD store. Use this option when you must completely rebuild the BCD.

Back to the top
APPLIES TO

    * Windows Vista Ultimate
    * Windows Vista Enterprise
    * Windows Vista Business
    * Windows Vista Home Premium
    * Windows Vista Home Basic
    * Windows Vista Business 64-bit Edition
    * Windows Vista Enterprise 64-bit Edition
    * Windows Vista Home Premium 64-bit Edition
    * Windows Vista Home Basic 64-bit Edition
    * Windows Vista Ultimate 64-bit Edition
    * Windows 7 Enterprise
    * Windows 7 Enterprise N
    * Windows 7 Home Basic
    * Windows 7 Home Premium
    * Windows 7 Home Premium N
    * Windows 7 Professional
    * Windows 7 Professional N
    * Windows 7 Starter
    * Windows 7 Starter N
    * Windows 7 Ultimate
    * Windows 7 Ultimate N
```

---

