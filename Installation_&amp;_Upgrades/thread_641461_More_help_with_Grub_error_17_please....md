---
title: "More help with Grub error 17 please..."
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Jabcor on 2007-12-15
I've been troubleshooting this for about 2 days now, starting with this thread:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

The scenario is that I have Windows XP, which was already  installed, on 1 hard disk. 

After installing Ubuntu I keep getting the error 17 message.


I've done the following so far (several times for some)

1. reformatted the partition and reinstalled Ubuntu.
2. Downloaded and ran Super Grub, which resulted in a variety of errors from:

When Attempting boot linux:

> Booting 'trying /boot/grub/menu.lst /grub/menu.lst /boot/grub/grub.conf /grub/grub.conf

selectfile /boot/grub/menu.lst /grub/menu.lst /boot/grub/grub.conf /grub/grub.conf

Error 15: File not found
  Booting 'not lucky'

pause SGD has NOT doen it :((
SGD has NOT done it :((


 
When I attempt a manual boot (did this twice with my AUTO and LBA options selected in BIOS)

> 

Booting '2 hda2 sda2 (hd0,1) hd0s2 Linux '
set out device =(hd0,1)
........
.......
...
configfile (hd0,1)/boot/grub/menu.lst

Error 18: Selected cylinder exceeds maximum supported by BIOS


I boot to Windows XP fine via Super Grub

3. Editied the  menu.lst and switched Windows and lunx (hd0,1) (not sure what to call this but flipped em)  This resulted in Win Xp booting up fine. 

4. Verified  my HD has priority
5. Made HD the primary boot device.
6.  Searched many forums and sites for fixes...


So --   can anyone point me in the right direction here?  

If more info would be helpful, please let me know what to provide.

Thanks!

---

### Post by Jabcor on 2007-12-15
I'm not sure if this extra info will help but:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfdb6fdb6

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           16065   187864109    93924022+   7  HPFS/NTFS
/dev/hda2   *   187864110   307387709    59761800   83  Linux
/dev/hda3       307387710   312576704     2594497+   5  Extended
/dev/hda5       307387773   312576704     2594466   82  Linux swap / Solaris

```

---

### Post by torgrot on 2007-12-15
Have you tried any of the suggestions on this page: [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

torgrot

---

### Post by psusi on 2007-12-15
Press e when the grub menu comes up to edit the command line.  There should be a line that says:

root (hd0,1)

If the 1 is something else, change it to 1 and then press b to boot.

---

### Post by Jabcor on 2007-12-15
> Have you tried any of the suggestions on this page: [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

torgrot


Did now and get new errors.  I can't even"boot directly to Linux" or whatever that option is.  Bout to just give up.

---

### Post by Jabcor on 2007-12-17
Here is something else.  I'm not sure if this is a similar problem or not, but I got the following error when I gave up on Grub and tried lilo:

no boot signature in partition

:popcorn:

---

### Post by logos34 on 2007-12-17
Is this an older computer?

---

### Post by Jabcor on 2007-12-17
Ermm, yes and no.  It is a pieced to gether machine.

------------------
System Information
------------------
Time of this report: 12/17/2007, 14:17:29
       Machine name: E2H
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
           Language: English (Regional Setting: English)
System Manufacturer: NVIDIA
       System Model: AWRDACPI
               BIOS: Award Modular BIOS v6.00PG
          Processor: AMD Athlon(tm) 64 Processor 3000+,  MMX,  3DNow, ~1.8GHz
             Memory: 2048MB RAM
          Page File: 508MB used, 3431MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode


Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 45.0 GB
Total Space: 105.3 GB
File System: NTFS
      Model: WDC WD1600JB-00REA0

      Drive: D:
      Model: SAMSUNG DVD-ROM SD-616Q
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 8/4/2004 00:59:52, 49536 bytes

(from the XP boot, dxdiag)



Is any of that the issue?  Would knowing the BIOS version help?

---

### Post by logos34 on 2007-12-17
Well, for one thing I just noticed there is a newer version of the firmware for your dvdrom. Need to update in windows, though:
[http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SD-616Q&mType=FM&dType=D&cttID=687943&prd_ia_cd=05050400&disp_nm=SD-616Q](http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=SD-616Q&mType=FM&dType=D&cttID=687943&prd_ia_cd=05050400&disp_nm=SD-616Q)

As to the main problem, I was thinking maybe it was possibly a bios limitation issue, but I doublt that's it.  
> System Model: AWRDACPI
BIOS: Award Modular BIOS v6.00PG

---

### Post by logos34 on 2007-12-17
If you tried the suggestions [here]("http://www.users.bigpond.net.au/hermanzone/p15.htm#17"), not sure what else to suggest.  Try [GAG bootloader]("http://www.users.bigpond.net.au/hermanzone/p12.htm")?

---

