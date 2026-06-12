---
title: "Cannot boot win8 after installing ubuntu 13.04 for dual boot"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by bestluckth on 2013-11-23
Hey,

I met the same issue and couldn't boot to windows 8 after ubuntu. Did the Boot-Repair recommended fix but the issue was not fixed. Here is the link [http://paste.ubuntu.com/6464413/](http://paste.ubuntu.com/6464413/). Any help is appreciated!

---

### Post by bestluckth on 2013-11-23
Hey,

I couldn't boot to windows 8 after ubuntu. Did  the Boot-Repair recommended fix but the issue was not fixed. Here is the  link [http://paste.ubuntu.com/6464413/](http://paste.ubuntu.com/6464413/). Any help is appreciated!

---

### Post by oldfred on 2013-11-23
Moved your other post in a solved thread. Users looking to help other users do not usually open a solved thread since it is already solved. And if solutions in solved thread do not help then  you new thread is more appropriate.

It looks like you deleted all the Windows boot files from the efi partition. You will need Windows repair flash drive to fix that as those are Windows files.

       Windows UEFI install should  have backup of bootmgfw.efi here, but you also need a BCD and some misc files that Windows normally installs:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Another user post this from his efi partition and those are the files you seem to be missing.

>  -rwxr-xr-x 1 root root 1601880 Sep 30 05:57 ./Microsoft/Boot/bootmgr.efi
-rwxr-xr-x 1 root root 1493344 Aug 22 15:45 ./Microsoft/Boot/memtest.efi
-rwxr-xr-x 1 root root 123904 Nov 17 14:37 ./Microsoft/Boot/bootmgfw.efi
-rwxr-xr-x 1 root root 123904 Nov 17 14:37 ./Microsoft/Boot/bootx64.efi



 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

It also looks like you deleted the Windows system reserved partition, which Windows requires.
       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

---

### Post by ptrakk on 2013-11-23
you might try testdisk to repair the System partition. also you may try this: [http://www.appassure.com/support/KB/4610043/](http://www.appassure.com/support/KB/4610043/)

---

