---
title: "Installation error, unable to access disks"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by Supernoobie on 2010-12-19
Hi all, I'm fairly new to Ubuntu/Linux. Here's the problem I'm encountering after I tried to install Ubuntu Desktop 10.10

I was installing from a CD, as I tried to install alongside Windows XP,  (The setup detected 2 hard drives, the first one was 40 GB, with all my  windows stuff on it, the other was a 160 GB one), I got the message  "error informing kernel about changes made to .....", which would not  disappear no matter what I clicked. So, choosing the seemingly only  option, I force powered down the computer. As I powered it back on,  Windows did not boot, instead I just got a black screen of nothing but a  flashing _. I tried booting from the LiveCD again, which worked well  enough, EXCEPT, the 40 GB hardrive full of my Windows stuff and files  was not detected, and the 160 GB drive was detected only in the drives  tool, but not accessible. I have no clue as to how to: 1. retrieve  important files from my 40 GB drive. 2. Restore Windows XP professional

PLEASE HELP :frown:

I will try to provide any information I can

---

### Post by Quackers on 2010-12-20
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Supernoobie on 2010-12-20
> **Quackers said:**
> Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   306,550,783   306,548,736  83 Linux
/dev/sda2         306,552,830   312,498,175     5,945,346   5 Extended
/dev/sda5         306,552,832   312,498,175     5,945,344  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by sikander3786 on 2010-12-20
I am sorry to say but what boot script out put tells us, there seems to be nothing on your HDD. No Windows install, no Ubuntu and no bootloader.

If there were some important files on your HDD which you want to recover, boot an Ubuntu Live CD/USB and try Testdisk.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Have you got Windows backup on CD/DVD? You'll probably need to re-install both Windows and Ubuntu.

---

### Post by Supernoobie on 2010-12-20
> **sikander3786 said:**
> I am sorry to say but what boot script out put tells us, there seems to be nothing on your HDD. No Windows install, no Ubuntu and no bootloader.

If there were some important files on your HDD which you want to recover, boot an Ubuntu Live CD/USB and try Testdisk.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Have you got Windows backup on CD/DVD? You'll probably need to re-install both Windows and Ubuntu.

How do I work Testdisk? Please give some instructions, as I have next to zero understanding of installing things on Ubuntu. Thanks

---

### Post by sikander3786 on 2010-12-20
Boot an Ubuntu Live CD. Applications > Accessories > Terminal:

```
sudo apt-get update && sudo apt-get install testdisk
```

Once installed,

```
sudo testdisk
```

And it might guide you after that. Step by step instructions here.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Supernoobie on 2010-12-20
> **sikander3786 said:**
> Boot an Ubuntu Live CD. Applications > Accessories > Terminal:

```
sudo apt-get update && sudo apt-get install testdisk
```Once installed,

```
sudo testdisk
```And it might guide you after that. Step by step instructions here.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I tried, but I get this
```
 E: unable to locate package testdisk
```

---

### Post by oldfred on 2010-12-20
the boot script is only showing the 160GB drive and it just looks like it it formated with nothing. Did you also have data on the 160GB drive?

But the script did not even see your 40GB drive. Does BIOS still see it?

---

### Post by sikander3786 on 2010-12-20
> But the script did not even see your 40GB drive. Does BIOS still see it?

I accept I missed that. Thanks **oldfred** :-)

To the OP: Your 40GB drive is not being detected and all your Windows stuff was on that one. Check your Bios settings. If it gets detected, you might be back in business.

---

### Post by Supernoobie on 2010-12-20
> **sikander3786 said:**
> I accept I missed that. Thanks **oldfred** :-)

To the OP: Your 40GB drive is not being detected and all your Windows stuff was on that one. Check your Bios settings. If it gets detected, you might be back in business.

I checked in the list of boot sequences, SATA Drive 1 is listed as (not present). I don't think I've used the 160 GB drive much. Testdisk detected 3 partitions in 160, but when I press p, no list of files come up. instead I get "ENTER: to continueAbandoned (core dumped)

---

### Post by sikander3786 on 2010-12-20
Did you search for any reason behind your Sata1 disappearing behind the scenes? What happened? Some loose cabling or the HDD just ran bad?

Regarding test disk, the recovery might or might not be successful. **Oldfred** are one of the most experienced members between us and they know testdisk very well. You may want to wait for their opinion.

---

### Post by oldfred on 2010-12-20
Did you have data on the 160GB drive you want to recover. Testdisk also has a deeper search that sometimes finds partitions, but you have to have some idea of what partition(s) you are looking for. Was your 40GB just a windows 'Drive' that was a partition on the 160GB drive?

If Testdisk does not work, then you can use photorec which is part of testdisk to recover files. But you have to have another drive to copy data to, and it does not recover file names as it is just scanning drive for data that looks like a file to recover. I had saved a text file many times and it recovered it many times and sometimes just parts of it, so it was some work to rebuild file. 

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by Supernoobie on 2010-12-20
> **oldfred said:**
> Did you have data on the 160GB drive you want to recover. Testdisk also has a deeper search that sometimes finds partitions, but you have to have some idea of what partition(s) you are looking for. Was your 40GB just a windows 'Drive' that was a partition on the 160GB drive?

If Testdisk does not work, then you can use photorec which is part of testdisk to recover files. But you have to have another drive to copy data to, and it does not recover file names as it is just scanning drive for data that looks like a file to recover. I had saved a text file many times and it recovered it many times and sometimes just parts of it, so it was some work to rebuild file. 

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

hm. that gets me thinking. It is possible that the 40 gig was a partition of the whole... testdisk deeper searched a 31 gig partion, which might be it. I'm not so sure. Should I try photorec before writing in testdisk?

---

### Post by oldfred on 2010-12-20
I do not think testdisk will damage anything, but you probably will not recover a bootable partition. You may be able to recover some files, but it depends on where data was written on what may be damaged.

The photorec takes hours even on a 160GB drive, and you have to copy the recovered files to another drive.

---

### Post by Supernoobie on 2010-12-20
> **oldfred said:**
> I do not think testdisk will damage anything, but you probably will not recover a bootable partition. You may be able to recover some files, but it depends on where data was written on what may be damaged.

The photorec takes hours even on a 160GB drive, and you have to copy the recovered files to another drive.

Ok, testdisk seems to have recovered a 34 GB partition, however, when I try to access it when booted into LiveCD, it tells me

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x1: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by Supernoobie on 2010-12-20
[IMG]http://farm6.static.flickr.com/5009/5279313942_53838754c5.jpg[/IMG]
[IMG]http://farm6.static.flickr.com/5210/5279313944_662333677a_z.jpg[/IMG]

screenshots :S

---

### Post by oldfred on 2010-12-21
Even if testdisk made it NTFS, NTFS partitions have to have the boot sector set up correctly. Test disk also has a function to rebuid the boot sector.
You also may have to run chkdsk which  only windows has. You need any version of windows repairCD to run chkdsk.

sudo testdisk
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot 

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.

---

### Post by Supernoobie on 2010-12-21
Well, it seems like I have found the Windows partition, although when i get to the windows logo screen, a blue screen pops up saying:
ERROR_UNMOUNTABLE_VOLUME

what do? :o

---

### Post by oldfred on 2010-12-21
Well since part of it was overwritten it will not be bootable. Can you run chkdsk or is it too damaged. Also can you mount it with Ubuntu?

Not sure if this is not just what we did.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by Supernoobie on 2010-12-23
> **oldfred said:**
> Well since part of it was overwritten it will not be bootable. Can you run chkdsk or is it too damaged. Also can you mount it with Ubuntu?

Not sure if this is not just what we did.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Hm. Can't mount it with Ubuntu. Whenever I try to repair MFT with testdisk, it tells me "Abandoned (core dumped). No clue what that means. 

I'll have to dig around for my windows CD :P

---

### Post by oldfred on 2010-12-23
If you are sure you have nothing important on the 160GB drive that was not otherwise backed up, we do not have to worry about it.

But the 40GB drive seems like a bigger issue. If BIOS does not see it we cannot do much. I would check that connectors have not come loose, not sure what else.

If drive is locked up, some have used either cold or heat or a bump to get drive spinning. It is often a one time try to restart drive. recover data, and then it is for sure gone. Sometime the issue is the lubricant in the drive is old and is just does not want to spin anymore. If it is other issues like electronics or reading head. How important is data on 40GB drive?

---

### Post by oldfred on 2010-12-23
So was the 40GB really just a partition on the 160GB drive.

Testdisk also has photorec. This just scans drive looking for anything that looks like a file. You have to copy data to another drive. It does not recover file names but photos & mp3's have internal data that you can use to recover a name. I had a text file that I had saved many times and it recovered many versions & some partial versions. Not sure if I ever got last saved but between backup and bits and pieces I recovered most of my text file.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by Supernoobie on 2010-12-23
I did photorec, and got back most of my word documents (about 30 % were corrupt) and nearly all of the PDFs, So i guess ill give chkdisk a try, if that doesnt work, then ill just format and go all ubuntu. Thanks for your time oldfred. :D

---

