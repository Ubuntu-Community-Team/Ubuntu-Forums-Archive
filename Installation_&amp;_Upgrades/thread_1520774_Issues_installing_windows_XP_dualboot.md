---
title: "Issues installing windows XP dualboot"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by MalioSwift on 2010-06-30
So I have a single hard drive with two partitions, and I am trying to install a dual boot of Windows XP and Ubuntu. However, I am having an issue installing the Windows XP component. 

I keep getting an error along the lines of a missing/corrupt hal.dll after the first restart in the install. This has happened every time I tried to install windows XP, from several different discs, all of which I have confirmed to work on another computer. 

I have tried several things for fixing this, from repairing the MBR and boot.ini to replacing hal.dll from hal.dl_, and nothing works. However, Ubuntu 10.04 installs and boots properly. 

Any suggestions on what I can do to get Windows to install properly?

---

### Post by dino99 on 2010-06-30
i left windoz over few years ago and i'm happy with this: dont need it any more ):P

install wine to run the .exe progs

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by Rubi1200 on 2010-06-30
> **MalioSwift said:**
> So I have a single hard drive with two partitions, and I am trying to install a dual boot of Windows XP and Ubuntu. However, I am having an issue installing the Windows XP component. 

I keep getting an error along the lines of a missing/corrupt hal.dll after the first restart in the install. This has happened every time I tried to install windows XP, from several different discs, all of which I have confirmed to work on another computer. 

I have tried several things for fixing this, from repairing the MBR and boot.ini to replacing hal.dll from hal.dl_, and nothing works. However, Ubuntu 10.04 installs and boots properly. 

Any suggestions on what I can do to get Windows to install properly?

I found this:

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Take a look at what it says about hal.dll and see if anything rings a bell.

Is XP currently installed?

Also, to check your general setup, boot from the Ubuntu CD choosing to try not install and then run the script I have linked to at the bottom of my post. Get the results back here and we can take it from there.

---

### Post by tommcd on 2010-06-30
> **MalioSwift said:**
> So I have a single hard drive with two partitions, and I am trying to install a dual boot of Windows XP and Ubuntu. However, I am having an issue installing the Windows XP component. 

Make sure you install Windows XP first. Install XP to the first primary partition on your hard drive, which will be formatted to XP's NTFS file system. Then after XP is installed install Ubuntu to the second partition. The linux partition(s) can be primary or logical. Install Ubuntu's grub to the MBR of the hard drive and you will be able to use grub to boot XP or Ubuntu.
This is how I have always done it.

---

### Post by varunendra on 2010-06-30
Follow exactly what tommcd said.

If even after that it returns the same error, download & run [boot info script]("http://bootinfoscript.sourceforge.net/") from terminal in Ubuntu & post the contents of result.txt here. (you can also do it right now, but tom's suggestion would be the solution in most cases anyway)

---

### Post by oldfred on 2010-06-30
+1 on Rubi1200 suggestion 

Another link with similar info:
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)

---

### Post by MalioSwift on 2010-06-30
> **dino99 said:**
> i left windoz over few years ago and i'm happy with this: dont need it any more ):P

install wine to run the .exe progs

[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

I realize I could do this, but I need to keep XP running to keep the missus happy, among other things. 

> **Rubi1200 said:**
> I found this:

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Take a look at what it says about hal.dll and see if anything rings a bell.


Went through all of this before posting, sadly no luck. According to the Hitachi Drive test linked at the bottom, there is nothing wrong with my hard drive either.

> **Rubi1200 said:**
> 
Is XP currently installed?


No, it gets halfway through the install, to the first time it has to restart, then gives me this error.  But it had installed fine several times before when I was using only XP, though now it won't even do that. 

> **Rubi1200 said:**
> 
Also, to check your general setup, boot from the Ubuntu CD choosing to try not install and then run the script I have linked to at the bottom of my post. Get the results back here and we can take it from there.

I shall try this next, after I get my coffee for the day. 

> **tommcd said:**
> Make sure you install Windows XP first. Install XP to the first primary partition on your hard drive, which will be formatted to XP's NTFS file system. Then after XP is installed install Ubuntu to the second partition. The linux partition(s) can be primary or logical. Install Ubuntu's grub to the MBR of the hard drive and you will be able to use grub to boot XP or Ubuntu.
This is how I have always done it.

This is what I am trying to do, actually. Just having issues with getting XP to install first.

Thanks for all of the responces. I shall try Rubi1200's script when I get a chance to, hopefully within an hour or two.

---

### Post by darkod on 2010-06-30
I can't help much with the error, just to point out that running the boot info script will probably be useless. It's designed to give info about the boot setup which helps a lot in troubleshooting dual boot.
You don't even have XP installed, let alone dual boot.
Have you changed any BIOS settings recently? Maybe it doesn't like if you changed something like SATA mode, IDE, AHCI, etc.
Also, don't try to create the partitions in advance with any other tool, maybe the XP installer didn't like that. Delete all partitions again, and create one single ntfs for the XP system partition using the XP installer. Of course, don't allocate all the disk to it, just the part you want for XP.
Maybe it will help.

---

### Post by MalioSwift on 2010-06-30
> **darkod said:**
> I can't help much with the error, just to point out that running the boot info script will probably be useless. It's designed to give info about the boot setup which helps a lot in troubleshooting dual boot.
You don't even have XP installed, let alone dual boot.
Have you changed any BIOS settings recently? Maybe it doesn't like if you changed something like SATA mode, IDE, AHCI, etc.
Also, don't try to create the partitions in advance with any other tool, maybe the XP installer didn't like that. Delete all partitions again, and create one single ntfs for the XP system partition using the XP installer. Of course, don't allocate all the disk to it, just the part you want for XP.
Maybe it will help.

I didn't think it would be of much use either, but I figured I'd try it

I have not touched any of the BIOS settings, so it shouldn't be that. 

I will try deleting all of the partitions and doing as you say. 

If it will help at all, this is what that script outputted. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c9a578f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   620,751,599   620,751,537   7 HPFS/NTFS
/dev/sda2         620,751,600   968,382,134   347,630,535  83 Linux
/dev/sda3         968,382,135   976,768,064     8,385,930  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc792c8eb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6b399121

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BAD495ABD4956B01                       ntfs                                     
/dev/sda2        2604ebee-aeb0-4456-9916-218650fbaf3b   ext2                                     
/dev/sda3                                               swap                                     
/dev/sdb1        C28CA9588CA9482D                       ntfs       Storage 2.0                   
/dev/sdd1        C64A9B8E4A9B7A3F                       ntfs       Storage                       
/dev/sde         10ED-D20F                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sde         /media/10ED-D20F         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=signature(8c9a578f)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
signature(8c9a578f)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by MalioSwift on 2010-06-30
So I tried deleting the partitions and letting Windows do it, and while I didn't get the same error, its now just going to a black screen after the first reset. Bleh. Any ideas?

EDIT: I changed to a different hard drive and it worked, which means it must have been something wrong with that hard drive. Any ideas on what could be wrong with it that Windows wouldn't install, but Ubuntu would?

---

### Post by darkod on 2010-06-30
> **MalioSwift said:**
> So I tried deleting the partitions and letting Windows do it, and while I didn't get the same error, its now just going to a black screen after the first reset. Bleh. Any ideas?

That's windows for you. :)

Are you booting from the windows disk? You might also try unplugging all other disks until you get this sorted out. Just in case.

I'm running out of ideas here. It can't even install itself properly. :)

---

### Post by MalioSwift on 2010-06-30
Yeah, I ended up disconnecting the rest of my hard drives and then switching out the hard drive, so I guess there is something wrong with this hard drive, though I can't imagine what would stop a windows install but allow an ubuntu install. If anyone has suggestions on how to fix that, that'd be great, cause I'm using a small spare hard drive at the moment.

---

### Post by varunendra on 2010-07-01
I'm writing this post through a PC whose HDD had apparently died 3-4 months ago. But now is running fine with Ubuntu since last three months (70+ % drive is full at the moment).
At that time it had WinXP installed on it and had (still has) too many bad sectors, caused by frequent power-failure. I tried installing Windows XP on different fresh-made partitions on it. It got installed & running every time, but would crash every 1 or 2 days returning errors like hal.dll missing, ntldr missing, 'system' file unreadable, registry corrupt........ etc.

I was sure it was due to bad blocks spread all over the drive. I tried zero-filling it which failed, then deleted all partitions & recreated them. To avoid unlikely chances of any virus-attack, I disconnected it from network & used it for offline works only. Didn't restore any backed-up data (again, to avoid the 'virus thing' ;)). Nothing helped, but yes, after every crash, XP got installed somehow with a few glitches & sometimes warnings.

Eventually I gave up & trashed the computer for 1-2 weeks waiting for arrangement of a new HDD. Meanwhile I stumbled upon some blogs discussing **fundamental difference between Windows & Linux filesystems** (which was a bit controversial about ntfs algorithm, but the idea clicked for me!).
The summary of the whole discussion ***[COLOR=DarkRed](see one [here]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting"), the most interesting one, especially the comments after the article)[/COLOR] ***was that **Windows tries to place files in a consecutive order, starting from the beginning, often leaving no space in-between, while linux file systems try to scatter them all over the disk for multi-user optimization. **

I had already assumed that the reason of failure of XP was due to concentration of bad sectors at the beginning of the disk (where system-files of XP are maintained), so influenced by the basic idea of the blog, I decided to give Ubuntu a try on the same HDD. It was the first time I dedicated a single-partitioned whole HDD to any linux OS. It's now more than 3 months now and I am more than happy with it. Power failures still occur, but have had no impact on the setup so far.
:) :) :) :)


Having told the above story and mixing it up with your situation, I assume that yours too is a problem with bad physical condition of the disk platters. If you happen to think like me then I'd suggest a few more shots you can try.

First, try zero-filling the drive with tools like Seagate's Disk-Manager and see if it completes successfully (it's very time taking). Although rarely, but I have seen it doing the magic in the past. Whether it succeeds or not, try recreating 3-4 equally-sized partitions choosing a 'full-format' option with tools like fdisk in DOS. **Then install XP in 2nd or 3rd partition**. Preferably choose the one that got formatted most smoothly (indicating a good surface condition).

If even that doesn't do the job, then perhaps installing Ubuntu & using XP in VirtualBox is the only alternative with that disk.

---

### Post by MalioSwift on 2010-07-02
Ah! That would explain it, probably. I'm probably just going to put just Ubuntu on it, to save myself trouble. I will probably switch between hard drives til I get the Ubuntu one settled, and the girlfriend finally gives in to using Ubuntu.

---

