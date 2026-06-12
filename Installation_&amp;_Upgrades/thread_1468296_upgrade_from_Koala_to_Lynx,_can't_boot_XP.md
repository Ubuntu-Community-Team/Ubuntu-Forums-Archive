---
title: "upgrade from Koala to Lynx, can't boot XP"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by mcallisto on 2010-05-01
Hi all,

I was starting from a perfectly working dualboot system with Koala and Windows XP.

Upgraded to Lynx, now GRUB sees the bootable partition
Microsoft  Windows XP Professional (on /dev/sda1)
but when I choose it then I have back screen with blinking cursor forever,

Some details:

 * fdisk /dev/sda returns:

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1    *           1        7337    58934421    7  HPFS/NTFS
/dev/sda2             7338       14593    58283820    5  Esteso
/dev/sda5             7338       14291    55857973+  83  Linux
/dev/sda6           14292        14593     2425783+  82  Linux swap / Solaris


*  if from GRUB I press "e" on Windows XP the settings are:
insmod  ntfs
set root='(hd0,1)'
search --no -floppy --fs -uuid --set  f8783fda783f95fa
drivemap -s (hd0) ${root}
chainloader +1

Any hint? Thank you in advance.

Best,

Mario

---

### Post by oldfred on 2010-05-01
Did you by any chance also install grub to sda1?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If this is not the solution:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mcallisto on 2010-05-01
> **oldfred said:**
> Did you by any chance also install grub to sda1?

Yes, it would seem so from the Boot Info Script. To be noted that, if I remember correctly, it was actually the upgrade process of Lynx to suggest if any doubt about where to install GRUB to choose the option to install it everywhere...

```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 118163648 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

```I'll try to fix it with the suggested solution, thank you, and will let you know if solved or not.

Best,

Mario

---

### Post by mcallisto on 2010-05-01
Thank you again, now solved, XP can be booted.
I followed exactly the proposed "testdisk" solution.

Best,

Mario

---

