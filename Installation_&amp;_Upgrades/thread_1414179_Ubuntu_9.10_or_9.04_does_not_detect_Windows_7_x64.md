---
title: "Ubuntu 9.10 or 9.04 does not detect Windows 7 x64"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by amsoares on 2010-02-23
I'd like to have a dual-boot system with WIN7 and Ubuntu. I already have Windows 7 installed. I tried the 9.10 installation but the partitioner says i don't have any Operating Systems installed. I read a few threads about this type of issue and i didn't find any solution. Then i found a discussion saying that there is a problem with GRUB2 in 9.10 and that the problem is not present in 9.04. Then i tried the installation with 9.04 but got exactly the same problem: the partitioner does not detect Windows 7. Basically i have this system:
- Windows 7 Professional x64
- 1 TB HDD with 4 partitions with 100Gb each (NTFS)
- ~600 GB unpartitioned free space
- Processor Intel Core 2 Quad Q8200
- ASUS P5Q MOBO
- ATI Radeon HD 4550
I tried both the x32 (i386) and x64 (AMD) versions of 9.10 and the x64 version of 9.04. I don't have the WIN7 partition that some installations seem to have, at least i don't see it under Disk Management (Computer Management).
 
Please help.
Thanks.

---

### Post by darkod on 2010-02-23
The maximum on a hdd is 4 partitions, which can either be 4 primary or 3 primary + extended for example.
If you have 4 partition you can't install ubuntu because a 5th one can't be created.
Reconsider your layout, you could for example combine the 3 current partition (without the system C: partition) into one extended (3 logical inside extended). That way the total will be 2, one primary for win7 system partition (which has to be primary) and one extended with 3 logical inside. Then you could create another extended to host ubuntu.

---

### Post by amsoares on 2010-02-23
Thank you very much for this. I was completely unaware of this. I will rebuild the layout as you suggested.

---

### Post by amsoares on 2010-02-23
Well, i thought i had 4 partitions but in fact i don't. I have only the Primary Partition (C:) and then an Extended Partition. Inside this Extended Partition i have 3 Logical Drives (D:, G: and H:). So the Ubuntu partitioner should see this and be able to recognize it, right ? But this doesn't happen. What could be the problem ?
 
Please assist.
Thanks.

---

### Post by darkod on 2010-02-23
> **amsoares said:**
> Well, i thought i had 4 partitions but in fact i don't. I have only the Primary Partition (C:) and then an Extended Partition. Inside this Extended Partition i have 3 Logical Drives (D:, G: and H:). So the Ubuntu partitioner should see this and be able to recognize it, right ? But this doesn't happen. What could be the problem ?
 
Please assist.
Thanks.

I don't know what could be the problem. Ubuntu needs to detect the windows boot files and that's how it knows it's there. If it can't, or the boot files are not there, it will look like you don't have windows installed.
The boot files seem to be allright, because it seems you can boot windows fine.

---

### Post by darkod on 2010-02-23
You could also follow these instructions here and post the content of your results file. It will show more detailed info about you boot process and OS.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by amsoares on 2010-02-23
darkod, thank you very much for trying to help me with this. I will run your script as soon as possible. In the meanwhile, do you see any problem with my partition table:
 
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63c563c5
Device Boot Start End Blocks Id System
/dev/sda1 * 1 12748 102398278+ 7 HPFS/NTFS
/dev/sda2 12749 50993 307202962+ f W95 Ext'd (LBA)
/dev/sda5 12749 25497 102406311 7 HPFS/NTFS
/dev/sda6 25498 38246 102406311 7 HPFS/NTFS
/dev/sda7 38247 50993 102390246 7 HPFS/NTFS
ubuntu@ubuntu:~$ 
 
 
Thanks.

---

### Post by amsoares on 2010-02-23
Here is the RESULTS.TXT output:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

---

### Post by darkod on 2010-02-23
The script is not able to recognize anything. Ubuntu too.

You could try checking the disk for errors in windows. Boot windows, open command prompt and run

chkdsk c:/f

That will check C: for errors. It might ask you to restart and it will do the check on the restart. I'm not sure what else to do.

---

### Post by amsoares on 2010-02-23
Well, the computer is brand new and i don't think i have hdd problems but i will do that. But there is a fact: fdisk correctly identifies the partitions but the Ubuntu partitioner does not. So there must be something wrong with the Partitioner. Is this GRUB2 ?

---

### Post by amsoares on 2010-02-23
The chkdsk gave me no errors at all. It seems there is a solution to this problem:
 
[http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html](http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html)
 
I would love to see an official explanation to this. Right now i'm not very interested in re-installing WIN7 from scratch.

---

### Post by amsoares on 2010-02-24
Guys, any comments to my previous post ? Maybe there is an workaround to the problem.

---

### Post by pmeves on 2010-02-24
Finally found someone with the same problem.

I have actually 3 partitions: system reserved from Win7 (100mb), C: where is installed windows 7 and another one with 40gb i let clean for ubuntu.

first trying to install ubuntu, i have two errors when reading the windows partitions, something like sda / dev0 don't really remember, but it's the partition used in grub to detect windows, in that case, windows partition. ( so it's logical that it wont detect partitions, given the error ). But why this? i tried to mess with bios hdd features etc, and still nothing.

some months ago it detected (before a bios update, don't know if it's related) and after instaling ubuntu, ubuntu touched win7 boot files and could no longer boot windows, saying it was missing files.

If someone got answers and/or solutions we are waiting.

PS: about the last post, i'm reading it and it's kind of impressive how many people have this problem. I ask one more time for users that know how to solve this, please help.

---

### Post by darkod on 2010-02-24
What they say in that article is not 100% in all cases. On my netbook I installed win7 wiping the hdd first, which means the small 100MB partition and the win7 system partition were created by the win7 installer.
Then booted with usb stick of 9.10 and it installed fine, it could see the win7 OS and added it to grub menu automatically.
I guess it can be a combination of reasons, but just because the partitions were created by win7 installer does not make them automatically not recognizable to ubuntu.

Unfortunately I don't know what more to say about your problems here. They really are strange.

---

### Post by pmeves on 2010-02-24
> **darkod said:**
> What they say in that article is not 100% in all cases. On my netbook I installed win7 wiping the hdd first, which means the small 100MB partition and the win7 system partition were created by the win7 installer.
Then booted with usb stick of 9.10 and it installed fine, it could see the win7 OS and added it to grub menu automatically.
I guess it can be a combination of reasons, but just because the partitions were created by win7 installer does not make them automatically not recognizable to ubuntu.

Unfortunately I don't know what more to say about your problems here. They really are strange.

You can say that... they are really strange. I once installed Win7 and ubuntu just fine, now seams like my problems are extending!

The previous tutorial to install it with a partition tool other than win7 tool seems to be ok, i should try that but it's not a real solution. we want to ubuntu recognizes it fine. thinking now better about the problem i think i know why this.
Maybe the win7 installation goes like the bios is set up. And i had some problems before with an option to hdd and OS's. Maybe reinstalling win7 with the option turned off and it would be recognizable... I have a feeling that could be the source for my problem.

this weekend i will try reinstalling everything like i said, and give some news. In case it will be ok, don't worry i got some other problems in ubuntu once i got the dual boot fine :popcorn:

---

### Post by darkod on 2010-02-24
> **pmeves said:**
> You can say that... they are really strange. I once installed Win7 and ubuntu just fine, now seams like my problems are extending!

The previous tutorial to install it with a partition tool other than win7 tool seems to be ok, i should try that but it's not a real solution. we want to ubuntu recognizes it fine. thinking now better about the problem i think i know why this.
Maybe the win7 installation goes like the bios is set up. And i had some problems before with an option to hdd and OS's. Maybe reinstalling win7 with the option turned off and it would be recognizable... I have a feeling that could be the source for my problem.

this weekend i will try reinstalling everything like i said, and give some news. In case it will be ok, don't worry i got some other problems in ubuntu once i got the dual boot fine :popcorn:

Creating ntfs partition with gparted for example in advance shouldn't be required. However, with win7 I did that for a friend to save him one primary partition because if there is existing ntfs partition that you want to use, the win7 installer doesn't create the unneeded 100MB boot partition. If you have a single disk and want to dual boot, it's better to save one primary partition for something else.
So, I didn't need to do it, but I wanted to create ntfs first with gparted and win7 installed on it just fine and it took only one partition.
As for BIOS, take a look at the SATA Type too. You chould use AHCI, I think that should be first option. The next would be Native IDE, and RAID shouldn't be used unless you are actually setting up the motherboard fakeraid.

---

### Post by pmeves on 2010-02-24
> **darkod said:**
> Creating ntfs partition with gparted for example in advance shouldn't be required. However, with win7 I did that for a friend to save him one primary partition because if there is existing ntfs partition that you want to use, the win7 installer doesn't create the unneeded 100MB boot partition. If you have a single disk and want to dual boot, it's better to save one primary partition for something else.
So, I didn't need to do it, but I wanted to create ntfs first with gparted and win7 installed on it just fine and it took only one partition.
As for BIOS, take a look at the SATA Type too. You chould use AHCI, I think that should be first option. The next would be Native IDE, and RAID shouldn't be used unless you are actually setting up the motherboard fakeraid.

Yes the Hdd has that option ( and it's the only one ). The option i was talking about, is for OS boot option. It asks if i want to enable the option to try first opening the main OS i think, like a grub choice. Don't really know what it means, but i know it has some influence over the OS...

For the partitions, i don't have a choice with win7 tool. once created the primary partition, it creates auto/ the 100mb reserved. So what you are saying is that it's better to have a primary partition without that system reserved space?

---

### Post by darkod on 2010-02-24
> **pmeves said:**
> Yes the Hdd has that option ( and it's the only one ). The option i was talking about, is for OS boot option. It asks if i want to enable the option to try first opening the main OS i think, like a grub choice. Don't really know what it means, but i know it has some influence over the OS...

For the partitions, i don't have a choice with win7 tool. once created the primary partition, it creates auto/ the 100mb reserved. So what you are saying is that it's better to have a primary partition without that system reserved space?

For me it is. Why creating 2 partitions when 1 does the job just as well. The choice you have is:
Decide how much space you want to give the win7 system partition (you can have another ntfs for data, I'm just talking about the system partition, C: ). Boot with ubuntu cd first, open Gparted and create one single ntfs partition with the size you want. Apply and close Gparted. Don't create any partitions for ubuntu at that moment, not needed. You will do that with the installer.
Then boot with the win7 DVD and start the installer. It will find the ntfs partition, just tell it to install there. In this case, when existing partition is used, it doesn't create the small 100MB one.
It's the same if you are installing over vista for example. You tell it to use the existing partition and it doesn't create the second one.
That way you save one partition for other purposes because the max on a hdd is 4 (primaries + extended, and inside an extended you can have more logicals).
About that option in BIOS, I haven't seen it yet, but if it's like you say, I guess it's best to be disabled. There is no need BIOS to try booting the main OS, it might be confused what your main OS is.
The boot should still be successful from hdd with this option disabled.

---

### Post by pmeves on 2010-02-24
> **darkod said:**
> For me it is. Why creating 2 partitions when 1 does the job just as well. The choice you have is:
Decide how much space you want to give the win7 system partition (you can have another ntfs for data, I'm just talking about the system partition, C: ). Boot with ubuntu cd first, open Gparted and create one single ntfs partition with the size you want. Apply and close Gparted. Don't create any partitions for ubuntu at that moment, not needed. You will do that with the installer.
Then boot with the win7 DVD and start the installer. It will find the ntfs partition, just tell it to install there. In this case, when existing partition is used, it doesn't create the small 100MB one.
It's the same if you are installing over vista for example. You tell it to use the existing partition and it doesn't create the second one.
That way you save one partition for other purposes because the max on a hdd is 4 (primaries + extended, and inside an extended you can have more logicals).
About that option in BIOS, I haven't seen it yet, but if it's like you say, I guess it's best to be disabled. There is no need BIOS to try booting the main OS, it might be confused what your main OS is.
The boot should still be successful from hdd with this option disabled.

OK thank you very much! i will see how i can do that but in fact your right why having this extra noneeded partition. for this Bios option, the best is that next time i reboot i take a note about it, to let it clear about what it is.

Meanwhile, if you know how i can put WLan and Bluetooth to work on my clevo w860cu (in ubuntu), i would really be gratefull.

Thanks :)

---

### Post by amsoares on 2010-02-24
Strange, i installed WIN7 on a unformatted disk and i don't have that 100 MB partition. I have WIN7 Professional x64. I will verify that BIOS setting to see what i have there.

---

### Post by darkod on 2010-02-24
> **amsoares said:**
> Strange, i installed WIN7 on a unformatted disk and i don't have that 100 MB partition. I have WIN7 Professional x64. I will verify that BIOS setting to see what i have there.

Just to remind you that you won't see it in Computer. Like any other system partition you might have. You need to look in Disk Management or in linux in Gparted, they show all partitions on the hdd.

---

### Post by amsoares on 2010-02-24
I don't have it. Check again the fdisk output:
 
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63c563c5
Device Boot Start End Blocks Id System
/dev/sda1 * 1 12748 102398278+ 7 HPFS/NTFS
/dev/sda2 12749 50993 307202962+ f W95 Ext'd (LBA)
/dev/sda5 12749 25497 102406311 7 HPFS/NTFS
/dev/sda6 25498 38246 102406311 7 HPFS/NTFS
/dev/sda7 38247 50993 102390246 7 HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by amsoares on 2010-02-24
In the BIOS, i see my SATA disk configured as IDE. Could this be related with the problems i have ? This is off-topic, but what happens if i change that to AHCI ?

---

### Post by darkod on 2010-02-24
> **amsoares said:**
> In the BIOS, i see my SATA disk configured as IDE. Could this be related with the problems i have ? This is off-topic, but what happens if i change that to AHCI ?

Personally, I have it as IDE too and it works fine. But there were cases here where changing to AHCI helped. It's just a setting how the system should view the hdd.

Yes, you don't have the 100MB partition, I forgot about the fdisk data.

---

### Post by pmeves on 2010-02-24
I checked the Bios and here's the option:

Legacy OS Boot:

Select Enabled to attempt Legacy OS Boot Only.
Select disabled to attempt EFI Boot first, Legacy OS Boot Second.


This option about IDE, sata, etc... Gave me some troubles with my asus laptop, the one i had before this clevo w860cu. You should check it and try different options...

---

### Post by amsoares on 2010-02-24
Guys, i found something interesting. If i run the Live CD (try ubuntu w/o modifications), the fdisk output shows correct partition information as well as gparted. Then after double-clicking the install ubuntu icon in the desktop, i arrive to step 4 where the partitioner says i don't have any partitions. After this, fdisk won't show anything and gparted doesn't even recognize the HDD. It's clear to me that there is a problem with the ubuntu partitioner. What partitioner is this ? Now i will repeat the process with 9.04 to see what happens.

---

### Post by amsoares on 2010-02-24
This is unbelievable! The same happens with 9.04 and 8.10. Is there any way to see the error messages the partitioner possibly gives ?

---

### Post by pmeves on 2010-02-25
> **amsoares said:**
> This is unbelievable! The same happens with 9.04 and 8.10. Is there any way to see the error messages the partitioner possibly gives ?

I don't know :(

It seems to me that this topic is moving through shadows, and we're not the only ones with this issue...

i just can try a new reinstall next weekend, then i will give some news.

I just can't wait the new ubuntu, because this one is simply leting me down! Intel WiFi Link 5100 drivers bugged for me, installation and ACPI events missing, just great.

---

### Post by darkod on 2010-02-25
> **amsoares said:**
> Guys, i found something interesting. If i run the Live CD (try ubuntu w/o modifications), the fdisk output shows correct partition information as well as gparted. Then after double-clicking the install ubuntu icon in the desktop, i arrive to step 4 where the partitioner says i don't have any partitions. After this, fdisk won't show anything and gparted doesn't even recognize the HDD. It's clear to me that there is a problem with the ubuntu partitioner. What partitioner is this ? Now i will repeat the process with 9.04 to see what happens.

I'm not sure if it can be related but if you have raid meta data settings remains on the hdd the 9.10 partitioner can detect them and it gets confused. But 9.04 shouldn't as far as I know.

If you are NOT running raid, just in case boot the 9.10 live desktop and execute:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

After that click the Install icon on the desktop and see if it helped maybe.

Another reason might be some strange format of the partition table, that somehow ubuntu can't recognize sometimes. But this is pure speculation, I wouldn't know how to explain it.

---

### Post by amsoares on 2010-02-25
Darko, i tried the procedure you mentioned but it didn't work. I will wait pmeves update to see if he is successful.

---

### Post by pmeves on 2010-02-27
2 hours now and here's what i got:

-Win7 64 MSDN did not boot ( so i took win7 final retail );

-Win7 final retail 64 did boot, formatted and cleared everything.
 Created 1 partition, automaticaly created 100mb system and i let free space for ubuntu -> exit;

-Boot ubuntu 9.10 64, it did not find any partitions -> exit;

-Put win7 MSDN dvd x64, it boot, format all again, created partition for windows and now here's where the things changed! win7 created auto 2 new partitions instead of one! system 100mb, MSR(reserved) 128mb, my primary C:, and the free space for linux -> exit;

-Ubuntu, install and... it found the partitions! -> exit ( i want to install win7 first for grub...)

-boot win7 64 msdn again, install in the C: all perfect -> exit;

-Now the Bios option made effect. I wanted to boot ubuntu and it just jumps the dcd and boot win7 (that was installed just before). Conclusion, the way win7 was installed in the new system partitions that it created before without me knowin why and how, now Bios can find win7 too and the option make it jump boot options and boots win7...

-Restarted and changed Bios option;

-Ubuntu did boot, found partitions but did not find win7 installed;

-Installed ubuntu and restart;

-Grub loading and... boot ubuntu. windows 7 has not been found and put in grub options. i'm now in ubuntu and shall see my grub file see if i can put windows 7 in it and boot it correctly, because last time this went like this, i had windows 7 in grub, but ubuntu messed my win7 boot files and i couldnt boot win7 anymore.

(- I don't have wireless, drivers bugs. Found this but did not try yet [http://www.linuxquestions.org/questions/linux-networking-3/intel-wifi-link-5100-cannot-work-on-linux-678588/](http://www.linuxquestions.org/questions/linux-networking-3/intel-wifi-link-5100-cannot-work-on-linux-678588/) )

(ACPI event for Bluetooth don't work like i was waiting for).

I will give some news about Grub. Still, ubuntu did not find windows 7 installed, but found partitions... now i dont really know how to change grub because i don't know where win7 boot files are! ( 3partitions created just to install it. I guess it's the C: partition, the primary) so I will try

---

### Post by pmeves on 2010-02-27
formated again and installed only win7. I can't do anything.

Grub is so different and it's not the 2.0... menu.lst does not exist etc etc... i tried but it gave me an error. tired of it, i tried win xp cd for the partitions, result : windows xp after loading files, give me a blue screen.

Vista created partitions were not detected by ubuntu, and ntfs partition created from gparted is a MSR partition for win7, so i cannot install windows in it, but need to if i want ubuntu to recognize win7 installed.

It's just all confusing. Win7 install boot files somewhere where ubuntu does not find them, and when i try to have just an only option like a single partition, i cannot put win7 in it.

Now, and after passing 8 hours around that, i have win7 all reinstalled, and a partition created for ubuntu, ready and recognizable, but win7 is not, so i won't install it, because if i do, I will have only ubuntu and won't be able to dual boot.

---

### Post by amsoares on 2010-02-27
Thank you for sharing your experience. Did you try the procedure described here ?
 
[http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html](http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html)
 
We must investigate deeper because i don't believe this is not possible to achieve. I don't want to delete WIN7 from my disk because i spent several hours to put everything as i like otherwise i would try the procedure above. I think it's the only information about someone that was able to dual boot WIN7 and Ubuntu 9.10. By the way, i tried the 10.04 (Alpha 3) installation and got exactly the same problem. From the live CD gparted and fdisk are able to recognize the partitions. But after running the installer, i get the same error with the partitioner saying i don't have partitions and hereafter gparted and fdisk don't recognize the partitions anymore.

---

### Post by meierfra. on 2010-02-28
**pmeves:**
I think your case is completely different than amsoares' .  Could you start your own thread? Please post your  [RESULTS.txt]("http://bootinfoscript.sourceforge.net/") in the new tread.

**amsoares:** 
Looking at the error messages on RESULTS.txt, there might be problem with your hard drive.  Go the website of the manufacturer of your hard drive and look for some tools to  check on the integrity of your hard drive.

---

### Post by pmeves on 2010-02-28
> **amsoares said:**
> Thank you for sharing your experience. Did you try the procedure described here ?
 
[http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html](http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html)
 
We must investigate deeper because i don't believe this is not possible to achieve. I don't want to delete WIN7 from my disk because i spent several hours to put everything as i like otherwise i would try the procedure above. I think it's the only information about someone that was able to dual boot WIN7 and Ubuntu 9.10. By the way, i tried the 10.04 (Alpha 3) installation and got exactly the same problem. From the live CD gparted and fdisk are able to recognize the partitions. But after running the installer, i get the same error with the partitioner saying i don't have partitions and hereafter gparted and fdisk don't recognize the partitions anymore.

Yeah I tried! as i said, i tried about everything. WIth Gparted i created 2 partitions, one of them ntfs, and when i went to win7 dvd , the partition is recognized as a MSR partition, a reserved partition, and cannot install win7 on it... Is there another way? ( 3. Create an NTFS partion (I used the first half of the disk) ) That's what i did.

---

### Post by pmeves on 2010-02-28
> **meierfra. said:**
> **pmeves:**
I think your case is completely different than amsoares' .  Could you start your own thread? Please post your  [RESULTS.txt]("http://bootinfoscript.sourceforge.net/") in the new tread.

**amsoares:** 
Looking at the error messages on RESULTS.txt, there might be problem with your hard drive.  Go the website of the manufacturer of your hard drive and look for some tools to  check on the integrity of your hard drive.

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/3570426/index/page/1](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/3570426/index/page/1)

---

### Post by meierfra. on 2010-02-28
**pmeves:** 
I meant a new thread in the Ubuntu forums (trying to solve two problems in one thread  can be very confusing).  Also follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt in the new thread

---

### Post by pmeves on 2010-02-28
> **meierfra. said:**
> **pmeves:** 
I meant a new thread in the Ubuntu forums (trying to solve two problems in one thread  can be very confusing).  Also follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt in the new thread

Oh sorry :-? I will do that when i have some time! thanks for the advice ;)

---

### Post by oldfred on 2010-02-28
amsoares what brand and type is this 1TB drive? Is it a new Western Digital green drive by any chance?

---

### Post by amsoares on 2010-03-01
Yes, it's a Western Digital WD10EADS disk. Any known issues with WD disks ?

---

### Post by oldfred on 2010-03-01
The slightly newer EARS has 4K sectors that adds confusion (emulates 512 for XP), your version should still be standard 512 sectors and not related to any of the issues.

---

### Post by pmeves on 2010-03-01
My problem can be followed here : [http://ubuntuforums.org/showthread.php?t=1419299](http://ubuntuforums.org/showthread.php?t=1419299)

thanks for the advice =)

---

### Post by darkod on 2010-03-01
Sorry to jump in, but I noticed you have GPT partition table. Did you try meierfra's fix for GPT:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

Although in that fix it's mentioned it's for mix of GPT and DOS partition tables. Also the instructions are for running from within the ubuntu install. Can you boot it?

If not maybe someone can help with chroot. Not sure if I can figure it out. And whether this fix can help.

PS. Plus you have no bootloader on /dev/sda, not even windows one.??? How can anything boot?

---

### Post by pmeves on 2010-03-01
> **darkod said:**
> Sorry to jump in, but I noticed you have GPT partition table. Did you try meierfra's fix for GPT:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

Although in that fix it's mentioned it's for mix of GPT and DOS partition tables. Also the instructions are for running from within the ubuntu install. Can you boot it?

If not maybe someone can help with chroot. Not sure if I can figure it out. And whether this fix can help.

PS. Plus you have no bootloader on /dev/sda, not even windows one.??? How can anything boot?

I wasn't quite sure if it's for me so I will create a new thread about my problem.

---

### Post by darkod on 2010-03-01
> **pmeves said:**
> I wasn't quite sure if it's for me so I will create a new thread about my problem.

Yes, that was a response to your results file. That's why separate thread was recommended, it gets confusing trying to help more than one person. :) For everyone.

---

### Post by meierfra. on 2010-03-01
> meierfra's fix for GPT:

That only applies for a mixture of GPT and MSDOS partition table,


**pmeves:**

> I will create a new thread about my problem. 

Great.
> And here are my results:


Could you also delete your RESULTS.txt  from this thread? Having two different RESULTS.txt in the same thread is really confusing.

---

### Post by amsoares on 2010-03-02
Guys, i don't believe it ! I installed EasyBCD 1.7.2 and i simply choosed the option "Write MBR". Then i loaded the LiveCD and Gparted was able to see the partitions. Nothing new here. But after running the installer, now the partitioner was able to detect Windows 7 !!! Since is quite late, i aborted the installation but i will continue this tomorrow. It would be nice if someone has an explanation to this.

---

### Post by amsoares on 2010-03-03
Well, i was claiming victory but i have the same problem again. Ubuntu partitioner is not able to detect the partitions. Then i repeated the process. Choosed the option "Write MBR" in EasyBCD and loaded again the LiveCD. And for my surprise it doesn't work ... What is going here ? Any hints ? By the way, the partitioner always stops at 47% for about 30 seconds or more and then i get the window saying there are no operating systems installed. I remember thatyesterday, when it worked, it also stopped at 47% but a few seconds later i saw the progress bar moving to 100%. So it seems there is like a timeout problem or something like that. For some reason, sometimes after the trick with EasyBCD, the partitioner works normally. I could try the installation when i get it working again but i'm not very confident about what could happen during the installation.

---

### Post by oldfred on 2010-03-03
My question would be did it convert your gpt drive to a MBR drive?

---

### Post by amsoares on 2010-03-03
How can i verify that ? I forgot to say but WIN7 stills boots normaly !
 
In the meanwhile i found this tutorial:
 
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)
 
I think i have MBR since i have an extended partition but i will verify later.

---

### Post by rben13 on 2010-03-03
I have a similar problem. My system originally had Windows XP set up to dual boot with Kubuntu. Then I installed Vista (this was a while back) and wound up using SuperGrub to get Windows Vista booting. I was hoping both Windows XP and Kubuntu would be available, and while I could boot into Kubuntu, something else I did messed up the display drivers and I never got around to fixing it.

Then I installed Windows 7, which went suprisingly well. Afterwards my booting was a 2 stage process, first I'd get a grub menu, then another OS selection menu, setup by Windows, I believe. But everything worked at least as well as it had with Vista.

Then, today, I decided to take the plunge and install Ubuntu. I told the installer to put the software on my removable 640G hard drive, leaving a 100G partition for Windows and using the rest for Ubuntu.

Unfortunately, now my computer won't boot properly. It locks up at the first grub menu. I'm booted off the LiveCD right now, hoping someone can give me some guidence. I guess I could use Windows 7 installation CD to fix up the Windows side, but I'm not sure what to do and really don't want to spend a long time reinstalling applications. (My data is, thankfully, backed up offline.)

Please help.

Thanks,
  Ray

---

### Post by oldfred on 2010-03-03
rben13:
Please see Post #37.

---

### Post by amsoares on 2010-03-03
I finally was able to install Ubuntu !!! Dual boot works like a charme ! EasyBCD helped, i have no doubts. For some reason, the "Write MBR" option has an effect on how the Ubuntu partitioner behaves. Thank you to all that contributed in this thread.

---

### Post by geoaxis on 2010-04-15
> **amsoares said:**
> I finally was able to install Ubuntu !!! Dual boot works like a charme ! EasyBCD helped, i have no doubts. For some reason, the "Write MBR" option has an effect on how the Ubuntu partitioner behaves. Thank you to all that contributed in this thread.

amsoares, I downloaded EasyBCD and tried to use the WriteMBR option (which appears in manage boot loaders) and no luck 

Can you post detailed instructions or screenshots to how you managed to di ti with EasyBCD.

---

