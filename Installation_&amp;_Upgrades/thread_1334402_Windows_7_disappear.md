---
title: "Windows 7 disappear"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by papi92 on 2009-11-22
Hi! I have a little problem with Ubuntu 9.10 and Windows 7. I used to have windows 7 and XP. I deleted the XP and in this partition I installed Ubuntu. In Grub there’s no Windows 7. I’ve added it in the menu but when I start it the system says that there’s no boot manager. Please tell me how to start Windows 7?

---

### Post by darkod on 2009-11-22
Before installing ubuntu you should have repaired the MBR with win7 bootloader. It will probably work if you do it now.

Using win7 dvd boot and select Repair This Computer option. That will find your win7 installation and write the bootloader to the MBR.
But that will destroy grub2. After that you will have to boot with the Ubuntu CD with Try Ubuntu option and restore grub2 to the MBR.

---

### Post by papi92 on 2009-11-22
Ohhh sorry! My error is: ERROR 22: No such Partition

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5485    44058231   83  Linux
/dev/sda2            5486       49056   349984057+   5  Extended
/dev/sda3   *       49057       60801    94341712+   7  HPFS/NTFS
/dev/sda5            5984       49056   345983841    7  HPFS/NTFS
/dev/sda6            5486        5983     4000122   82  Linux swap / Solaris

Windows 7 is in sda3...

I add this in the menu.lst

title        Windows 7
root        (hd0,3)
savedefault
makeactive
chainloader    +1

Where is my mistake?

---

### Post by darkod on 2009-11-22
Grub2 that comes with 9.10 doesn't use menu.lst, how come you have that file?

Anyway, if you want to try and if you are using grub1 the line in menu.lst should be root (hd0,2). It counts the partition starting from 0. But only in grub1.

---

### Post by papi92 on 2009-11-22
I'm with GRUB 1.5... I install Ubunto 8.10, after update to 9.04 (with update manager) and then to 9.10

try with:
title        Windows 7
root        (hd0,**2**)
savedefault
makeactive
chainloader    +1

and the resuly was Boot Manager error

---

### Post by papi92 on 2009-11-22
Any ideas? I need the windows because in it there are programs like OrCAD with which i work...

---

### Post by oldfred on 2009-11-22
When you deleted XP you also deleted the boot files for the Win7 partiton:

Vista/Win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by papi92 on 2009-11-23
Thanks oldfred :)

---

