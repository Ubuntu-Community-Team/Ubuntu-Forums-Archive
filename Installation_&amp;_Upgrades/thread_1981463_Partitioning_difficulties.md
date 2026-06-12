---
title: "Partitioning difficulties"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by AnonymousJustified on 2012-05-16
Hello. I am planning to double-boot Ubuntu from my Windows XP, and evantually, if I like it enough, remove Windows entirely and use WINE for critical points of my current Windows setup.
But for now, I'm just struggling through the install process. I am typing this through the trial OS loaded on the Ubuntu disk. I know it will work with my computer, but I'm having trouble partitioning properly.
The simple issue is that it simply isn't allowing me to allocate my free space to a separate partition.
I am attempting to use Gparter to partition my free space from Windows. This is my first attempt at doing something like this, so I may be missing a step.

Thank you for your time.

---

### Post by VMC on 2012-05-16
It would be helpful if we can see how your hard drive is setup right now then advise on how to proceed.

One thing I would do is shrink down Windows and add linux partitions after Windows. You will need at least 1 partition for linux and you should have another partition for swap space.

The problem with windows is it like to have the first partition. Which is ok. linux is picky.

What I always want to see first is the layout. So if you could, download bootinfoscript. Run it as super user from you livecd. It will dump a file called RESULTS.txt. bring that back here so we can see how your currently partitioned and size of hard drive.

see my blue link below for location of bootinfoscript. Go [HERE]("http://bootinfoscript.sourceforge.net/") for a brief example on how to run it. Note the name has changed to *bootinfoscript* and not *boot_info_script.sh*.

---

### Post by AnonymousJustified on 2012-05-16
> **VMC said:**
> It would be helpful if we can see how your hard drive is setup right now then advise on how to proceed.

One thing I would do is shrink down Windows and add linux partitions after Windows. You will need at least 1 partition for linux and you should have another partition for swap space.

The problem with windows is it like to have the first partition. Which is ok. linux is picky.

What I always want to see first is the layout. So if you could, download bootinfoscript. Run it as super user from you livecd. It will dump a file called RESULTS.txt. bring that back here so we can see how your currently partitioned and size of hard drive.

Err... I'm a little new to tinkering with files, folders and OS configuration in general. I'm more used to programming with enclosed sandbox environments, VS most other stuff with a computer.

I'm more used to the Windows way of doing things, so, um, what, exactly should I do?

---

### Post by oldfred on 2012-05-16
If you click on VMC's link to the bootinfo script in his signature, it will take you to a page with instructions and a green button to download a bash file. You have to run from LInux preferably Ubuntu, either a liveCD, USB or full install. 

Since it can be long we like you to use code tags to preserve formating and make it easier to review. When you copy to your message, highlight again like copying and click on the # in the edit panel above your message. (full message not quick).

---

### Post by AnonymousJustified on 2012-05-17
Ugh...

sudo bash ~/Desktop/boot_info_script.s
HOLD IT! Okay, I figured out how silly I am now. Here we go.


Take note that "gawk" could not be found, so I'm using "busybox awk" instead.
This may lead to unreliable results.
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F0A4AC2AA4ABF170                       ntfs       Hard Disk
/dev/sdb1        208A-3F1C                              vfat       JEFF
/dev/sr0                                                iso9660    Ubuntu Linux

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Hard Disk         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/JEFF              vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------


```

---

### Post by VMC on 2012-05-17
Anonymous,

I uploaded my partitioning(see attachment) for "gparted". I have Windows on the first partition, another NTFS on the second. Both are primary partitions. My Linux installs are inside an Extended partition, as is my swap partition.

Don't worry so much about the number of installs as to how its allocated. Linux OS's work very well inside Extended partitions.
That will free up Primaries for other use, such as BSD slices.

Just study the diagram and ask any questions. From that livecd, you should have "gparted". Run it to get an idea of how it works. You would need to confirm any actions, so no worries.

When you feel comfortable enough, you can use "gparted" to shrink your Windows partition down to size.

My sda2 ntfs & sda9 ext4are use to store backups, downloads, and the like.

Another great tool for backing up your OS's is [Clonezilla]("http://clonezilla.org/"). You need to consider backing up your Windows partition first, before you do anything else.

---

### Post by AnonymousJustified on 2012-05-17
Well, for some odd reason, it seems to be working now. You did kinda misunderstand my issue in your post, but THAT problem is fixed, and now I have another thing to ask.

You just saw the information of my partitions, which I assume also means that you saw how much free space I had. I should be able to make a 20G partition to run Ubuntu. The main reason I want to run this in the first place is because Linux machines are generally faster. Also, I'm a bit of a cheapscape, using a computer until smoke is billowing out of it. My goal is not to get into the technical aspects, my goal is to run a safe, secure, fast system on an old machine. Granted, there are the inevitable technical things, and I will have to overcome them, but I think I wont need BSD or anything of the sort(correct me if I'm mistaken.).
So, all I need to do is make a 20Gig partition on my hard drive, this way I can load Ubuntu into it, without worrying about deleting Windows... That is, yet.

I may be taking the wrong approach here, and if you think I'm looking at this the wrong way, please tell me flat out. But, all I need is to be told how to make the partition and then I'm happy for a while.

---

### Post by oldfred on 2012-05-17
It does not show free space, just that you have wubi installed inside the NTFS partition which takes up the entire 80GB drive.

With Windows you need to keep 30% free inside the NTFS partition or Windows starts to slow down. Of course when you delete wubi, it will give you some more space.

I have always partitioned in advance. But just to see what it does I used a liveCD and let it auto install. It found 40GB of unallocated space and just installed.

So you should be able to use gparted to shrink XP, run chkdsk & defrag first. Then you can just use the auto install. If you want other than the default / (root) and swap (not sure how it chooses size) then you do have to manually partition but now can do that as part of the install under Something Else.

If you have something in your Wubi install you can move it to your partitioned install.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by AnonymousJustified on 2012-05-17
Thanks, but the issue with removing wubi is that it wont allow me to boot from the LiveCD after I uninstall, due to the fact that my Dell A08, I believe, BIOS don't have an option for CD-Rom boot.

Can I just run the Autoplay in Windows to install it, or something?

---

### Post by oldfred on 2012-05-17
I have heard that some computers make you both set BIOS to boot CD/DVD and also select using one time boot key to actually make it work. Is this one of those computers?

---

### Post by AnonymousJustified on 2012-05-18
> **oldfred said:**
> I have heard that some computers make you both set BIOS to boot CD/DVD and also select using one time boot key to actually make it work. Is this one of those computers?
Actually, after manually uninstalling Wubi, I read somewhere that if you put the .iso file for your version of Ubuntu in the same folder as Wubi.exe, it doesn't need to download the files.

This basically fixed my whole problem; The main cause was that Wubi.exe was having difficulty retrieving the files from the server, but that basically fixed it.

I'm glad to have my new install of Linux Ubuntu now, and am proud to declare this solved.

Cya next time I inevitably run into problems! ):P

---

