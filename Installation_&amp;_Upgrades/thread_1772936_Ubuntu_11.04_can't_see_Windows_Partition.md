---
title: "Ubuntu 11.04 can't see Windows Partition"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by MarkieMice on 2011-06-01
Well, as the title says, Ubuntu can't see my Windows 7 partition.  It says "No OS detected", or something along those lines.  I've gone into windows, and created a partition to install Ubuntu into.  It's a 50GB partition.  I left the partition as raw, and it still can't see it.  When I go into Disk Utility, however, it sees the NTFS partition, and the system reserved one.  I can also see the unformatted 50GB.

Any help would be appreciated.

---

### Post by dozycat on 2011-06-01
I had a similar problem with the dvd in ubuntu 11.04 64 bits.
And my dvd worked once I changed in the bios the sata mode from ide to AHCI mode.
I read around the bugs there was an error in ubuntu 10.10 with sata 3.0 in ide mode, it looks like is the same in ubuntu 11.04.

---

### Post by Quackers on 2011-06-01
MarkieMice, welcome to UF!
I am a little unclear about what you are trying to do.
Do you want to install Ubuntu via WUBI (the Windows/Ubuntu installer) or on a separate partition of your hard drive?

---

### Post by MarkieMice on 2011-06-01
dozycat, my current SATA mode is AHCI.  If I change it to IDE, Windows bluescreens.  I've no idea why.  

Quackers, I'm trying to install Ubuntu onto a new partition onto my drive.  Thanks for the warm welcome!

*edit: I'm booting from a USB device, if that makes any difference.  An SD card, to be exact.

---

### Post by Mark Phelps on 2011-06-01
> **MarkieMice said:**
> dozycat, my current SATA mode is AHCI.  If I change it to IDE, Windows bluescreens.  I've no idea why...
That's because you installed Windows when the drive was in AHCI mode -- and it's using those drivers.  If you switch to another mode, those drivers can't read the drive anymore.

Don't know if the Ubuntu installer can "see" a drive in AHCI mode -- which presents you a problem.  If you have to switch to IDE mode to install and run Ubuntu, then you won't be able to use Windows.

---

### Post by MarkieMice on 2011-06-01
Is there a way to somehow change or update the Windows drivers to read IDE instead of AHCI?

---

### Post by Quackers on 2011-06-01
When you say "Ubuntu can't see my Windows 7 partition", where are you when that happens? In the live cd/usb desktop? Have you run the installer?

---

### Post by MarkieMice on 2011-06-01
> **Quackers said:**
> When you say "Ubuntu can't see my Windows 7 partition", where are you when that happens? In the live cd/usb desktop? Have you run the installer?

I'm in the Live USB desktop.  Yes, I've run the installer.  I also tried running the GParted Partition Manager.  GParted sees my drive as a 320GB unallocated drive.  I'm sure this is not the case, as I can boot into Windows.

*edit:  Here's a picture.  I know I'm bad at explaining things.  :P

[IMG]http://farm6.static.flickr.com/5061/5786976722_5d267e4888.jpg[/IMG]
[IMG]http://www.flickr.com/photos/63545014@N05/5786976722/in/photostream/[/IMG]

---

### Post by Quackers on 2011-06-01
Ok, thanks.
Is your hard drive using a sata 3 port? 
Do you know what sata controller is in use?
Are you running a raid array?

---

### Post by MarkieMice on 2011-06-01
No, it's not SATA3.
What's a SATA Controller?  Is it the AHCI/IDE thing?  I'm using AHCI.
I'm not using RAID.

---

### Post by Quackers on 2011-06-01
Thanks.
You said earlier that you created a 50GB partition from within Windows.
How many primary partitions were in use by Windows before you created that new one?
The hardware isn't a Mac is it?
Sorry about all the questions, but I'm trying to figure out what's happening :-)

---

### Post by MarkieMice on 2011-06-01
No problems about the questions.  Data, data, data, as they say.  

I'm using a Gateway NV48.  It's not Mac-ed.  There were three partitions in Windows, the one with the actual Windows data, one that was used for 'System Reserved', and of course, the raw 50GB.  

I get the sort of feeling I'm not allowed to be using AHCI mode to install Ubuntu.

---

### Post by Quackers on 2011-06-01
AHCI works fine on mine :-)
I'm wondering whether the creation of the partition may have gone badly.
From the live desktop please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by MarkieMice on 2011-06-01
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 120704 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   522,739,711   522,532,864   7 NTFS / exFAT / HPFS
/dev/sda3         522,739,712   625,137,663   102,397,952   6 FAT16


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D054FBAB54FB9308                       ntfs       System Reserved
/dev/sda2        DE48FD4D48FD2545                       ntfs       
/dev/sda3        ee0f6760-4757-42eb-ac68-a70da0fdffe5   ext4       New Volume
/dev/sdb1        F009-64A5                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/DE48FD4D48FD2545  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by Quackers on 2011-06-01
The line below is where your problem lies

"GUID Partition Table detected, but does not seem to be used."

Is there any specific reason why you are using a GUID partition table?

---

### Post by MarkieMice on 2011-06-01
Umm.  No.  I didn't even know I had one.  What can I do about this?

---

### Post by Quackers on 2011-06-01
Hmm, good question :-)
If your system came this way there is likely to be a reason for it. Is there any software in your Windows system that needs EFI to boot (like a boot booster)?

It is possible to convert from GPT to MBR, though it is not something I have done.
Forum member srs5694 has written a page on his website regarding this issue.
I suggest that you have a read through that first.

Please also take note that a successful conversion to MBR automatically requires that no more than 4 primary partitions be created. However, one of these primary partitions can be an extended partitions, which can hold many logical partitions. So you are not actually limited to just 4 partitions (just 4 PRIMARY partitions).

[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

You want the Converting from GPT to MBR section, but you should read it all, really.

---

### Post by MarkieMice on 2011-06-01
I will.  Thank you very much for your help.  Do you think maybe it's got something to do with me installing VMWare on Windows?  I tried virtualizing MacOS.  It didn't work, though.

---

### Post by Quackers on 2011-06-01
It's got nothing to do with VM. Interestingly though, MacOS uses EFI, but I don't think that installing it in VM would affect you. But I've been wrong before! :-)

---

### Post by srs5694 on 2011-06-01
The disk is ***not*** currently a GPT disk. You've got *leftover* GPT data -- perhaps the disk was once used in a Mac, or an attempt was made (and then abandoned) to install OS X on it, or you experimented with GPT under Linux or some other OS, or perhaps you even bought the disk used or as an "open box" item and the previous owner used it with GPT. In any event, if the old GPT data isn't completely wiped from the disk, it confuses some utilities -- most importantly, most utilities based on libparted (including GParted).

The solution is to erase the old GPT data. This can be done in various ways, but the simplest is probably to use my [FixParts](http://www.rodsbooks.com/fixparts/) program. When you launch it on the disk, it will ask if you want to wipe the old GPT data. Answer in the affirmative and then quit from the program. The GPT data will then be gone.

---

### Post by Quackers on 2011-06-01
Aha! Thanks for your expert ministrations srs5694 :-)
I forget that fixparts does that! I must store that bit of information somewhere :wink:

---

### Post by MarkieMice on 2011-06-01
Haha.  Thank you to both of you, I've managed to get the installer to see Windows!  I used gdisk to convert the GPT to MBR.  Wasn't as scary as I thought it would be.  Thanks again!

---

### Post by Quackers on 2011-06-01
That's good :-) That was quick!
Have fun!
Don't forget the 4 primary partition limit on the MBR system!

---

### Post by srs5694 on 2011-06-01
> **MarkieMice said:**
> Haha.  Thank you to both of you, I've managed to get the installer to see Windows!  I used gdisk to convert the GPT to MBR.  Wasn't as scary as I thought it would be.  Thanks again!

I'm glad it worked, but that was probably risky. Given your disk, gdisk would probably give you an option of reading either GPT or MBR data. It would then set up an internal (in-memory) representation of the data as GPT. It's also got an option to convert GPT to MBR, which you say you used. Thus, one of two things could happen in the conversion you described:


[list]
[*]gdisk would convert MBR to GPT and then convert GPT to MBR (wiping the old GPT data in the process). This would work, but you might lose or change some data, such as boot flags and even MBR type codes. FixParts would wipe the old GPT data much more directly, with much less risk of damaging or changing the MBR data.
[*]gdisk would load the old GPT data, which might be anything, and then convert that to MBR and overwrite your valid MBR partitions. If you were very very lucky, the old GPT data would describe identical partitions to the MBR partitions that replaced them, in which case everything would be OK. Otherwise, you'd have trashed your partition table, requiring recovery from a backup of the partition table or use of a tool such as TestDisk.
[/list]


Since you say it's working, I'm not advising you do anything at this point. I just wanted to highlight the fact that using gdisk in this situation and in this way was risky, in case somebody comes along in the future, reads this thread, and decides to try the same thing. Such a person should post a new thread to ask for advice, since partitioning problems that look superficially similar can actually be very dissimilar.

---

