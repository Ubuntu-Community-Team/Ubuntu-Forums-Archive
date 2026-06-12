---
title: "USB Ubuntu formatted my Windows to ext4 without my knowledge"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by joshuayip on 2016-09-13
Hi guys, 

I was absolutely thrielled with ubuntu 16 recently released as I was finally able to install it into a 32GB USB drive (not live usb, but full installation). However just few days I discovered that my laptops Windows 7 on NTFS is no longer bootable. Finding is strange I opened up Gparted and released the Windows 7 hard disk is now a ext4 with linux swap just like how my thumbdrive is partitioned. 

I am not sure what caused this. I suspect it was because there was not enough space in my 32GB thumbdrive and ubuntu started to look for additional space in the hard disk and did this by cloning itself into the harddisk (like the casper-rw 

I am not sure how I can better explain this. My question now is how do I recover the Window 7. Ubuntu is now storing about 400MB of data in the hard disk. My USB is about 24GB / 32 GB full. I suspect there is not much left after the swap space. 

Please advice. Thanks

---

### Post by newbie-user on 2016-09-13
Sounds like you accidentally set your windows partition to be the swap space for the Ubuntu install. A default Ubuntu installation only takes up about 5-6GB, so there was (still is) plenty of space on the thumbdrive. I don't know if it's possible to recover the old Windows partition anymore. Good luck.

---

### Post by oldfred on 2016-09-13
Ubuntu does not auto clone itself, you at some point did another install if it overwrote the Windows install. Sometimes drive order by device like /dev/sda changes in BIOS and if not careful you can choose incorrect drive.

Only boot from flash drive or flash drive installer.
If any part of NTFS partition was overwritten, you will not be able to recover a bootable system. But you may be able to get some data back with effort. Best just to reinstall and restore from your backup.

Testdisk will show old partitions on drive. It may show multiple versions if changed several times. If you are lucky deeper search may show files. But if not you have to use photorec and that only finds files by extension and you have to manually sort and rename back to whatever name you had.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS
[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 

Some that use Windows suggest that Windows tools work better for NTFS recovery. Not all are free.
      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 
    [URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

---

### Post by joshuayip on 2016-09-19
> **oldfred said:**
> Ubuntu does not auto clone itself, you at some point did another install if it overwrote the Windows install. Sometimes drive order by device like /dev/sda changes in BIOS and if not careful you can choose incorrect drive.



I may have changed the BIOS boot order , tweaked it a bit when the USB 3.0 port was not working 100% of the time. I thought my USB3.0 port burnt out or something. When I put it on the USB2.0 port it booted without issue. 

However during this process, I tweaked the bios boot order. That may have triggered it. Is there any way I can "write protect" the hard disk to avoid this from happening again ?

---

### Post by oldfred on 2016-09-19
With Linux you can set permissions to be read only, but then you cannot use drive to write anything.

Many suggest disconnecting other drives. Other say just to be careful.

And always have good backups.

---

