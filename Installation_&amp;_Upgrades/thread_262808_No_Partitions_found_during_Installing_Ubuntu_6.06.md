---
title: "No Partitions found during Installing Ubuntu 6.06"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Baseilos on 2006-09-22
Hi, please help me , I am a newbie. 
I wanna install Ubuntu 6.06 (Dapper Drake) 64Bit version, but Installator can't find partitions on my HDDs (Maxtor , Samsung, S-A TA TYPE). LiveCD boots up normally , my HDDs are listed in Administration->Disks, but no partitions are found. I tried both installations (Text,GUI) but nothing helped. I also tried to create an EXT3 partition manually, but it didn't solve problem.
Does somebody know where can be a problem & how to solve it ? 
Thanks a Lot

PS: My PC : AMD Athlon 3000+ 64Bit
            Asus K8N4-E Deluxe
            512MB RAM 400Mhz
            MAXTOR (80GB),SAMSUNG(160GB) S-ATA HDDs.

---

### Post by carontis on 2006-09-22
I haven't understood if you want to install on an hdd alone or if you have to partiton it 'cause another system is there. Are 2 different things. Anyway you should check also your hdd behind if the jumper is well set, and for this it should be on MASTER (if you use that one as master/primary boot hdd); partitions will be created just booting from CD and after you gave all necessaries infos. When it will ask you if you want to erase all disk, give YES and wait, it will create them for you. Just follow what is asked and shown. If you need to make partitions, leave enough space for Ubuntu and possibly as first partition.

---

### Post by Baseilos on 2006-09-22
ok , but there is an another problem ,i a have two HDDs , on one i have WXP and 2nd is erased and when istallation asks where ubuntu should be installed , nothing appears , no partitions or HDDs names , simply nothing. Also a Gnome Partition Manager shows nothing. I looked into Adminstration->Disk , and there are my HDDs listed, but if i click on Partitions Bar, there is an annoucement -> "No Partitions Found on Device".

---

### Post by carontis on 2006-09-22
Try to unplug (phisically: cable and electrical) your hdd where you have the system installed and give to the new you'll be using the position of primary master and install on it, following what I told you before. You should have possible way to do everything. I ask you only 1 thing: where do you want to install exactly Ubuntu? On the 80 Gb or the other?

---

### Post by Baseilos on 2006-09-22
Firstly , i want to thank you for your patience :).
So , i want to install ubuntu on 160GB HDD , i have created new partition (50GB) formated EXT3(I want to install linux on this partition), other partitions are formated to NTFS. This HDD is set in BIOS as SECONDARY MASTER. I'll try to plug  out the PRIMARY HDD and i'll try to istall ubuntu. Thanks

---

