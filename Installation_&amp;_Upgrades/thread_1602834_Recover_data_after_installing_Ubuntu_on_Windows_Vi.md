---
title: "Recover data after installing Ubuntu on Windows Vista machine"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by tech707 on 2010-10-21
Hi folks, 
       I just got done installing Ubuntu 10.10 on my Windows Vista as  a separate partition and now my Vista wont boot (in fact I am not  seeing an option to choose another OS, every time it defaults to Ubuntu)
 I really dont want to loose all my data on Vista (I tried sudo fdisk and all Its only displaying one partition). How do I get my Vista  back? 
 Is it possible to at least recover my old data if not complete vista?
 Steps I took:
 From Windows, Disk management, I create a 30 GB  partition.
 Booted Ubuntu using USB and then picked this newly create  partition for install.
 picked mount point as "/" 
 Also checked the Format  option while installing.

Thanks.

---

### Post by The_Mad_Hatter on 2010-10-22
sounds like you accidentally formatted the entire hard drive.

---

### Post by oldfred on 2010-10-22
STOP using computer. The more data you write the less data you may be able to recover.

If you are showing only sda1 with fdisk, the first part of the partition has Ubuntu, but it is a lot smaller than Vista. You may be able to recover some files. But any data that has been overwritten is gone.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by tech707 on 2010-10-22
Thanks Oldfred.
    I will try this and post the results. Will close my thread then. Thank you very much.

---

