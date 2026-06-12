---
title: "Failure When Attempting to Dual-Boot with Windows 8"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by pulse89 on 2013-04-18
Ok, I tried installing Ubuntu 12.10 and when installing I  went to click on Something Else to install to a pre-made partition but  when I clicked on continue I realised I either missed (don't laugh) or  the mouse didn't click properly but it went straight to formatting and  trying to do a complete install. Luckily just as it started formatting  there was an error and in my panic I didn't think to write it down.  After exiting the installer I checked to see if my windows partition was  still ok, thankfully it was and I could still see and access  everything. I then re-started my laptop to try and boot back into  windows 8.


  No dice, I get the error Media Check [Fail] and I can now only boot  up using Live Ubuntu, I tried installing Ubunutu on a seperate 8.5GB  partition I had but no dice there either.


  Tried using Boot-Repair and that failed as well but here is the Info Summary for it [http://paste.ubuntu.com/5717818/](http://paste.ubuntu.com/5717818/)
  Is it possible to fix without using a Windows recovery disk? I just  have to hunt around for one is all. Also it would be good to keep my  files but it's not absolutely necessary.

EDIT: Is it worth giving the MBR recovery a go through Boot-Repair? It does say it could make things worse though...

Also here is the output of fdisk -l if it helps at all

      

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8b60314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdb: 16.1 GB, 16055795200 bytes
255 heads, 63 sectors/track, 1952 cylinders, total 31358975 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31299583    15648768    c  W95 FAT32 (LBA)



---

### Post by oldfred on 2013-04-18
With Windows 8, UEFI, secure boot, and UltraBoot it takes a bit to install.

You only have a MBR, so old partition tools like fdisk do not attempt to modify the new gpt type partition table.

From the BootInfo report you erased Windows. What is now sda2 may be parts of the old Windows install, but with Windows 8 secure boot you have many partitions which are not shown.

You can see if testdisk will restore old partitions. But it looks like you erased recovery partition also. And where ever your Ubuntu install wrote data damaged Windows data. You probably have to order a new Windows recovery disk from your computer vendor, some only charge minimal fees.


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

IF you want to attempt to use testdisk to restore, STOP using hard drive, only work from live installer.


 repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by pulse89 on 2013-04-21
[COLOR=#444444][FONT=Ubuntu Beta]Thanks for your answer. After investigating and digging around for quite a while, trying everything I could (everything only the recovery disk), I decided the damage to the file system was too extensive to repair and chose to just do a complete format and re-install as I couldn't afford the time to go digging around for another few days. Next time I give this a go I will be sure to read the links you have provided to ensure this doesn't happen again![/FONT][/COLOR]

---

