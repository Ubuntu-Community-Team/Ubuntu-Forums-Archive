---
title: "Grub 2 Problem On Triple Boot"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Mauka on 2009-12-09
Hi,

 I am trying to install a triple boot system (Windows 7, MAX OSX and Ubuntu 9.10). I have set up partitions for each of the OS and installed Windows 7 and MAC without a problem. However when I installed Ubuntu it discovered the other 2 OS's and created a suitable menu. The problem was when I selected the Windows option from the menu Windows reported a corrupted boot file. I then used the windows install DVD to repair the corrupted file. This in turn caused the GRUB menu to disappear as the machine would go straight too windows, and the only way I could get to the MAC OS was using a boot cd. 

I then reinstalled the Ubuntu OS but the same thing happened i.e. the GRUB menu listed the OS but any attempt to boot into Windows resulted in a corrupted file error. I am guessing that I will have to redo all the installs again but before that I thought I'd ask if anyone has any suggestions on how to recover the existing installs. Below is the output from the Partition inspector utility which I installed on the Mac.

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     40318019  Basic Data
 3       63324200    167919655  Mac OS X HFS+
 4      168181800    168183753  Unknown
 5      168183754   1069305831  Basic Data
 6     1941453286   1953523021  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1   1953525167  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 2, type Basic Data

Partition at LBA 63324200:
 Boot Code: Unknown, but bootable
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+

Partition at LBA 168181800:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Unknown

Partition at LBA 168183754:
 Boot Code: Unknown, but bootable
 File System: ext3
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 1941453286:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap


```

I have tried to recover the grub loader after repairing the corrupted file problems in Windows by using the live CD but despite following the instructions [ here ](http://ubuntuforums.org/showthread.php?t=1014708), nothing changed.
And even if it was recovered it looks like GRUB would just corrupt the Windows installation again.

Any suggestions would be most welcome,

Thanks
M.

---

### Post by shredder12 on 2009-12-10
grub recover should work.. did you upgrade grub after doing the install..
```
sudo update-grub
```
and post the output generated after running this command..

---

