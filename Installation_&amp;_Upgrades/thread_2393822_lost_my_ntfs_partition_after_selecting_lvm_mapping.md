---
title: "lost my ntfs partition after selecting lvm mapping"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by aelhosiny on 2018-06-08
Guys,

I have samsung EVO SSD
I had 2 NTFS partitions one with windows 10, another for storage, one ext4 with ubuntu 16.04 and a swap partition
I was installing ubuntu 18.04 where I selected something like LVM mapping.
After installation, I found that the whole disk turned into one partition and I can not see my NTFS paritions.

So please I need urgent help here to recover my partitions or at least important data !!

---

### Post by aelhosiny on 2018-06-08
Any help guys :(

---

### Post by coffeecat on 2018-06-08
Please be patient. You need to wait a lot longer than 40 minutes. The person who can help you may be in a completely different time-zone. If you don't get a reply after about 12 hours, it is OK to bring your thread up to the top by posting the single word "bump".

---

### Post by oldfred on 2018-06-08
LVM install is a full drive erase option.
STOP using install, as you are erasing more & more as you use it. Only use live installer.

You will not recover Windows, but with lots of effort may be able to recover some data.
Best just to reinstall and restore your data from your backups.

I only lost one folder and it took (older slow system) overnite to run photorec and then it only recovered file by type not full file name. So I had to compare to somewhat older backup copies and that took weeks. And I had to have a large drive to copy data to, even though I only wanted some of it.

The Linux tools are testdisk & photorec, but some with Windows say the Windows tools work better, but you may have to pay for best alternative.

       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery
[/URL][https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)

 [URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step
[/URL]
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
Caution: getdataback is not the same and is a scam. [URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

### Post by aelhosiny on 2018-06-08
OK,

I tried photorec but it seems restoring files previously stored to linux paritions. I created a windows bootable usb, installed windows 10. Should try now recuva.
During windows installation, I created a single windows partition. Left the rest of the drive unallocated. Should I format as well to ntfs ? Or it's better to reduce write operations  and leave it un-allocated ?

---

### Post by oldfred on 2018-06-08
If you installed Windows, then you have erased most of the remaining data on drive.
Windows NTFS likes to put data at beginning of drive, so old data and new install are now in mostly the same location. 

Never used Recuva, but it should be run from a working Windows install and you plug in damaged drive to that system. You cannot recover data once overwritten.

---

