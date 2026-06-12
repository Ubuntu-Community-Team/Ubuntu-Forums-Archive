---
title: "natty narwhal doesnt detect my windows7"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by abre on 2011-05-27
hi guys. i am newbe in ubuntu. i have lenovo g450 and has installed windows 7 ultimate for a long time ago. i want to try ubuntu natty in my lenovo with dual boot system. after loading natty disk and click on install ubuntu it said that this computer currently has no detected operating system and i have to choose erase disk and install ubuntu or something else. Could someone help me why the natty cant detect my windows 7? thanks a lot. i have created drive c with 50 gb for dual boot

---

### Post by Hedgehog1 on 2011-05-27
The most likely causes are:

[1] You made more than 4 primary partitions using the Windows Disk Manager, and it changes the partitions to an type that Linux does not (yet) understand)

[2] You have a mix of partition tables.

To figure out what you actual situation is, please do this so we can see what your options for installing might be:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by abre on 2011-05-28
thanks [Hedgehog1]("http://ubuntuforums.org/member.php?u=1230016"), this is the result

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 1273. But according to the info from fdisk, 
                       sda6 starts at sector 178270208.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 1273. But according to the info from fdisk, 
                       sda7 starts at sector 198750208.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   102,591,089   102,384,242   7 NTFS / exFAT / HPFS
/dev/sda3          78,043,770   488,392,064   410,348,295   f W95 Extended (LBA)
/dev/sda5         102,594,560   178,268,934    75,674,375   7 NTFS / exFAT / HPFS
/dev/sda6         178,270,208   198,748,159    20,477,952   7 NTFS / exFAT / HPFS
/dev/sda7         198,750,208   324,284,415   125,534,208   7 NTFS / exFAT / HPFS
/dev/sda8         324,286,464   488,392,064   164,105,601   7 NTFS / exFAT / HPFS

/dev/sda2 overlaps with /dev/sda3

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90F82BB7F82B9B0C                       ntfs       System Reserved
/dev/sda2        0C9E70E49E70C7AA                       ntfs       SYSTEM
/dev/sda5        02C47CEFC47CE677                       ntfs       ENTERTAINMENT
/dev/sda6        4ECA12C2CA12A66D                       ntfs       DATA
/dev/sda7        5EFC2D38FC2D0C39                       ntfs       HOBI
/dev/sda8        1C88A08E88A0684A                       ntfs       SOFTWARE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

### Post by abre on 2011-05-28
oh my god :( i dont understand that all

---

### Post by coffeecat on 2011-05-28
> **abre said:**
> oh my god :( i dont understand that all

Fortunately, there are people here who do.

I'll repost your boot info script output in code tags, because it is difficult to read otherwise.

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 1273. But according to the info from fdisk, 
                       sda6 starts at sector 178270208.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 1273. But according to the info from fdisk, 
                       sda7 starts at sector 198750208.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 [COLOR=Red]  102,591,089[/COLOR]   102,384,242   7 NTFS / exFAT / HPFS
/dev/sda3[COLOR=Red]          78,043,770[/COLOR]   488,392,064   410,348,295   f W95 Extended (LBA)
/dev/sda5         102,594,560   178,268,934    75,674,375   7 NTFS / exFAT / HPFS
/dev/sda6         178,270,208   198,748,159    20,477,952   7 NTFS / exFAT / HPFS
/dev/sda7         198,750,208   324,284,415   125,534,208   7 NTFS / exFAT / HPFS
/dev/sda8         324,286,464   488,392,064   164,105,601   7 NTFS / exFAT / HPFS

[COLOR=Red]/dev/sda2 overlaps with /dev/sda3[/COLOR]

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90F82BB7F82B9B0C                       ntfs       System Reserved
/dev/sda2        0C9E70E49E70C7AA                       ntfs       SYSTEM
/dev/sda5        02C47CEFC47CE677                       ntfs       ENTERTAINMENT
/dev/sda6        4ECA12C2CA12A66D                       ntfs       DATA
/dev/sda7        5EFC2D38FC2D0C39                       ntfs       HOBI
/dev/sda8        1C88A08E88A0684A                       ntfs       SOFTWARE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
```I've highlighted the problem in red. This is serious, and reflects an error in the partition table which needs editing. This is why the Ubuntu installer cannot see any operating system. Normally, I would suggest one of a couple of ways to correct this, but in a situation like this where the beginning of an extended partition is overlapping the end of a primary partition, it is difficult to decide whether to "move" the extended or primary partition. Is the end sector figure of sda2 wrong, or the start sector of sda3? My guess is the start sector of sda3 is the wrong one, but I'm not sure and I would like to see a more expert opinion.

Don't do anything just yet. I will pm an expert who will be able to better advise.

**EDIT**: I forgot to ask. Did the machine come with Windows pre-installed or did you install Windows yourself? And if the latter, did you use a 3rd party partitioning tool, and if so which one? Something has made a mess of your partition table and it would be useful to know what this was so that it can be avoided.

---

### Post by abre on 2011-05-28
i installed windows by myself. to make more space in drive C (to be 50 gb) i used minitool partition wizard profesional edition 6.0

---

### Post by srs5694 on 2011-05-28
It's almost certainly the extended partition that's malformed. /dev/sda2 ends shortly before /dev/sda5 begins, so it seems unlikely to me that /dev/sda2 is too big for the filesystem it contains (although that's a possibility). Even if that's the case, it's safe to fix it by adjusting the extended partition. The easiest way to do this is with my [FixParts](http://www.rodsbooks.com/fixparts/) program. Its Web page describes its use. Be sure to check that it's correctly detected all your partitions with "p" (except for the extended partition, which the program discards and then re-writes). Note that there's a version of FixParts for Windows, so you can run it from Windows before installing Ubuntu.

It's extremely important that this problem be corrected immediately. The way the partition table is written now, there's a danger that a write to /dev/sda2 could overwrite the start of the extended partition, which would cause you to lose all your logical partitions. This risk is low on a per-write basis, but the longer you use the disk, the more likely it is that damage will occur.

*After* you fix the problem, I recommend running Windows CHKDSK on /dev/sda2. There's a chance that whatever tool caused this problem ended up damaging that partition's contents. CHKDSK will detect any structural problems, but it won't detect damage to a file (which is more likely). It's unlikely that more than one file was damaged.

---

### Post by abre on 2011-05-28
hi srs5694, if i use fixpart to solve my problem, i worry that it can damage my system (sda2 in C drive). If it is happen, can i install windows on that? or the C drive will damage forever, so i cant use it anymore

---

### Post by abre on 2011-05-29
anibody home???? please someone help me???

---

### Post by coffeecat on 2011-05-29
> **abre said:**
> hi srs5694, if i use fixpart to solve my problem, i worry that it can damage my system (sda2 in C drive). If it is happen, can i install windows on that? or the C drive will damage forever, so i cant use it anymore

> **abre said:**
> anibody home???? please someone help me???

@abre, srs5694 is in a different time-zone - from me at least - so isn't likely to respond for some time. I'll answer your query as best I can in the meantime.

All that fixparts does is to rewrite the partition table which, in an mbr scheme, is in the first sector of the hard drive, in bytes 446 to 511 (counting from zero). Therefore it doesn't touch your sda2/C: partition, and in no way could it "damage" it forever. However, rewriting a partition table is a fundamental task. Which is why you should backup everything you can before doing anything that affects partitions. That being said, many people on this forum (myself included) have used fixparts and found it to be reliable and effective.

When you say "damage forever", you need to distinguish between damaging the filesystem in the partition and physically damaging the hard drive. Software like fixparts cannot damage the hard drive. And I can't see how fixparts could ever damage the sda2 filesystem, but it would be best if srs5694 commented on that.

So - if the worst came to the worst, you could indeed reinstall Windows to sda2, but you still need to repair the partition table inconsistency first. Both srs5694 and I have stated, in different ways, that this is a serious issue and needs to be fixed. It doesn't matter whether you install Ubuntu or not - this is still a matter needing attention.

Good luck with that. Read srs5694's link carefully. If you have any questions, just post back.

---

### Post by abre on 2011-05-29
i have download fixpart from [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/). i placed all files after extracted in C:/users/download. after click twice on gdisk.exe, i have attention like this:
[INDENT]GPT fdisk (gdisk) version 0.7.1
most version of windows cannot boot from a GPT disk, and most varieties prior to Vista cannot read GPT disks. Therefore, you should exit now unless you understand the implications of converting MBR to GPT, editing an existing GPT, or creating a new GPT disk layout!
are you sure you want to continue? (Y/N) :
[/INDENT]What i must to do, can you give me details what i must to do, step by step? thanks

---

### Post by srs5694 on 2011-05-29
> **abre said:**
> i have download fixpart from [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/). i placed all files after extracted in C:/users/download. after click twice on gdisk.exe, i have attention like this:

You did *not* download FixParts; you downloaded GPT fdisk (gdisk), a related but different program. Download FixParts from here:

[https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/)

As to your earlier questions, coffeecat's response was basically correct. FixParts should not write to within any of your primary or logical partitions, and so should not damage their contents. There is a caveat, though: Any program can contain bugs. I don't know of any in FixParts that would cause data loss, but I'd be a fool if I claimed that I know for a fact that such a bug does *not* exist.

That said, given the nature of the problem with your partition table, I'd say the risk of continuing to use those partitions (/dev/sda2 in particular) is far greater than the risk of running FixParts, even without backing up your data. As I wrote before, an unlucky write to /dev/sda2 could cause all your logical partitions to disappear.

Also, one expansion on something coffeecat wrote: The first sector of the hard disk does hold the primary partition table, as coffeecat said; however, logical partitions are defined in sectors scattered about the disk, with each partition's definition pointing to the next one in the chain. That's why your current setup is so dangerous; the definition for /dev/sda5 lies inside the space reserved for /dev/sda2, so writing in the wrong sectors of /dev/sda2 will render /dev/sda5 inaccessible; and if this happens, all the logical partitions after /dev/sda5 will also disappear. The point, though, is that FixParts (or any program that modifies logical partitions) must write to the sectors that define the logical partitions, so FixParts does modify more than just sector 0.

---

### Post by abre on 2011-05-29
hi srs5694, i'm so sorry my english is not good enough so i dont understand much about fixparts tutorial. after i lauch fixparts with administrator previlage, there is command prompt that said type device filename, or press enter to exit. what i must write on to solve my problem. what the meaning of # fixparts /dev/sdc as in fixparts tutorial? thanks

---

### Post by Quackers on 2011-05-29
That is an example.
Are you running fixparts from within Windows, from within Ubuntu or from Ubuntu live cd desktop?

---

### Post by abre on 2011-05-29
within windows in c drive

---

### Post by srs5694 on 2011-05-29
If you run FixParts in Windows, the device filename is "0:". You would open an Administrator command prompt window and type:

```

fixparts 0:

```

You *must* run the program as Administrator.

Once the program is running, do this:

```

FixParts 0.7.1

Loading MBR data from /dev/sdc

MBR command (? for help): **p**

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 15654912 sectors (7.5 GiB)
MBR disk identifier: 0x000721DC
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    62      6125599   primary     Y        Y      0x83
   5               6125662     15650907   logical     Y        Y      0x83

MBR command (? for help): **w**

Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): **y**
Done writing data!

```

I've put what you type in bold. The "p" command displays the partition table. In this example, I've got two partitions, one primary and one logical. (FixParts does not display extended partitions.) Your display will obviously be different, but you should use "p" to verify that all your partitions are present and marked as either "primary" or "logical" (*not* "omitted") in the "Status" column. If everything looks OK, type "w" to save your changes. If you see anything suspicious, type "q" to quit without saving and post the output here for advice.

---

### Post by abre on 2011-05-29
i'm sorry i still confused. after i run fixparts with run as administrator and show up command prompt, i must write fixparts 0:, after write that words what i must to do, if i press enter, the comand prompt is disappeared.

---

### Post by srs5694 on 2011-05-29
You run a *command prompt* as Administrator, and type "fixparts 0:" *in the command prompt window*. Alternatively, you could run fixparts directly as Administrator and enter "0:" when it asks you what device to use.

---

### Post by abre on 2011-05-30
ok srs5694, i have run all and everything be ok again. i can install ubuntu with dual boot. thanks man, you are good. hedhog1, coffecat and you srs 5694 and others thank you.

---

