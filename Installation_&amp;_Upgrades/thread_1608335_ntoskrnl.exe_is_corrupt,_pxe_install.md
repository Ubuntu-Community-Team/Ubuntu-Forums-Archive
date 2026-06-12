---
title: "ntoskrnl.exe is corrupt, pxe install"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by benner on 2010-10-28
I am dual booting a lab of 30 machines in an elementary school. They already have XP installed and I don't want to mess with that.  I certainly don't want to have to go to each one with a windows CD to 'repair' each one if this goes wrong.

So i tested on one (installed through PXE) and Ubuntu boots fine but I am getting:

'ntoskrnl.exe is corrupt' errors now.  I can't move on until I sort this out.  Any help is appreciated.

---

### Post by benner on 2010-11-05
bump

---

### Post by Mark Phelps on 2010-11-05
Sorry, but as evidenced by the lack of response -- this is an Ubuntu form -- not a Windows XP forum.  If you're in dire need of XP support and are waiting on that, this is the WRONG place to get it.

You might try asking your question in a Windows 7 forum (sevenforums.com) or you can take your question to MS Technet forums.

---

### Post by benner on 2010-11-08
#1) Installing ubuntu corrupted Windows, making it an Ubuntu issue.  I believe that the vast majority of Ubuntu users are, in fact, dual booters so it should be of some concern to the Ubuntu community if the process of installing Ubuntu messes up their systems and makes them unable to access their existing Windows systems.

#2)  As stated, this is an installation in a computer lab at a school.  If you have any interest in increasing the Ubuntu user base, you would be well advised to do what you can to support educators that are willing to put the time and effort into getting it into the hands of kids.

#3)  Why would you capitalize the word 'wrong' unless you were trying to make me feel stupid?  Are you trying to help or chase me away?

Mr. Phelps, I looked you up.  It seems that you have been pretty helpful on these forums.  I found quite a number of posts where you did indeed help people solve their dual boot problems and a number of other Windows-related issues.  

I have now tested on 3 machines and am continuing to get the same error.  Doesn't look like a Windows problem to me. Grub, maybe?

---

### Post by benner on 2010-12-01
Bump

I guess this will be my last try.  I have a lab full of XP machines and I want to dual boot them with Ubuntu.  If I am unable to do so without mucking up my XP systems, I won't bother.  XP runs fine.  I just wanted to introduce my students to something different.  i anyone has any idea why, or would like to help me find out why I get these errors, I would be most grateful and you will be guaranteed a lot of kids will get an opportunity to try your favourite distro.

---

### Post by soldier1st on 2010-12-01
ubuntu should not corrupt anything. when you installed ubuntu how did you and where did you put it and the grub boot loader? also is the ubuntu install 64bit or 32bit? also did you change any bios settings?
[Mark Phelps]("http://ubuntuforums.org/member.php?u=311399"): i do partially agree with you but since he installed Ubuntu then that makes it a valid ubuntu question as ubuntu is involved, surely you have some knowledge of that Windows they call it(lol) that could be put to use in helping the op.

---

### Post by benner on 2010-12-14
I just accepted the defaults for everything.  

Even installing from CD, I am still getting the same errors.  There is something about Grub2 and these machines, I guess.  But it is clearly not a Windows issue.  They boot fine, I install Ubuntu by whatever means (PXE or CD) then XP no longer boots but Ubuntu does.  Therefore, something about the process of installing Ubuntu screwed up my previously fine XP installation.

So on the newest one, here is what i get from Grub when I click 'e':

insmod part_msdos
insmod ntfs
setroot+'(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2268f51e68f4f181
drivemap -s (hd0) ${root}
chainloader +1

Which is quite different from the last time I had to edit a grub menu.  I have changed various values here and there but don't see any difference.

Even if I have to install Ubuntu one by one with a CD on each machine, I would like to be able to get this to work.  What seems to be the problem?  Any suggestions?

---

### Post by Mark Phelps on 2010-12-14
Sorry about not responding sooner ...

Thought you were only asking for help in repairing XP.  Didn't realize that it was a dual-boot situation.  SO, sorry about the "WRONG" comment ...

I didn't catch HOW you were installing Ubuntu.  IS it (1) by shrinking an existing XP partition, creating a new one (or leaving the space unallocated) and then installing Ubuntu in its own partition, or (2) using Wubi to install inside XP.

I'm guessing it's (1) -- in which case, you're probably using the Ubuntu installer to shrink the XP partition to make room.

There have been LOTS of reports of that shrinkage corrupting Vista/Win7 partitions, but not of XP partitions.

To give us a look at what you're up against, enter the following in a terminal "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

---

### Post by benner on 2010-12-14
Thanks for getting back.  

I have installed on a handful of the machines and gotten the same result on all but one.  In a couple cases, I resized a partition.  But yesterday, I just installed to one of the existing partitions.  There was a C;, D, and F: and a couple of gigs unallocated.  I reformatted and installed to F: without resizing, then made the unallocated space into swap.  

I am going to guess that if I throw in my XP disk and fixmbr then I will lose grub, right?

I read someone else that had the same problem with grub2 and switched to mint because it used an older version of grub. if this is the case it seems like a hassle for me to install ubuntu, use a windows cd to fix the mbr then reinstall grub, then do it all again 27 more times.

I will post fdisk in a couple hours when i get to work.  cheers.

---

### Post by benner on 2010-12-14
here is fdisk output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1caa00e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    92550464    46275201    7  HPFS/NTFS
/dev/sda2        92550465   125612234    16530885    7  HPFS/NTFS
/dev/sda3       125612235   156296384    15342075   83  Linux
/dev/sda4       156297216   156301311        2048   82  Linux swap / Solaris

---

### Post by Mark Phelps on 2010-12-15
> **benner said:**
> ...I am going to guess that if I throw in my XP disk and fixmbr then I will lose grub, right?
Right ...

> I will post fdisk in a couple hours when i get to work.  cheers.

Don't see anything wrong there -- just confirms that you're installing to separate partitions, not using Wubi.

As to multi-machine deployment, can't help there as I have no experience doing that scale of installations.

---

### Post by benner on 2010-12-16
Well, I am on the right track but still need help.  I managed to boot into Windows by repairing the MBR.  I did it from within Ubuntu using ms-sys:

sudo apt-get install ms-sys

sudo ms-sys -m /dev/sda

(I got it from here: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/))

Then I tried rebuilding GRUB and it went back to the supposedly corrupt ntoskrnl.exe error.  I tried replacing Grub2 with legacy Grub and am still getting the same errors.

Apparently i can instead install grub to the partition where Ubuntu is, then add Ubuntu to the Windows bootloader instead but that is a real hassle, especially if I have to do it on a roomful of computers, then explain it to the network administrators who will be maintaining it.

Hoping for a simpler solution.  What do you think is going on?

---

### Post by benner on 2011-02-04
bump

---

### Post by bcbc on 2011-02-04
Can you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") on the computer?

---

### Post by Ramla on 2011-06-28
> **bcbc said:**
> Can you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") on the computer?

Anybody who doesn't want to help an Arch Linux user on Ubuntuforums shouldn't read more.

Even if the original poster has decided he's had enough, I still don't want to be dependent on Windows bootloader. I have the exact same kind of problem. Last time I bought a hard drive I left room for Windows and now I finally decided to install it for some games. Windows booted fine after installation but I instantly had to install grub to go download me some ethernet drivers. Then ntoskrnl.exe failed me. I've tried replacing it and fiddling with menu.lst and boot.ini settings but nothing seems to help. Here's my bootinfoscript results.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    41,945,714    41,945,652  83 Linux
/dev/sda2    *     41,945,715   104,888,384    62,942,670   7 NTFS / exFAT / HPFS
/dev/sda3         104,888,385 1,953,520,064 1,848,631,680   f W95 Extended (LBA)
/dev/sda5         104,888,448   314,616,959   209,728,512   6 FAT16
/dev/sda6         314,617,023   318,617,144     4,000,122  83 Linux
/dev/sda7         318,617,208 1,953,520,064 1,634,902,857  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8d01f754-262a-43b8-bfce-2cc6e97723d5   ext4       juuri
/dev/sda2        AA2C35482C3510B5                       ntfs       
/dev/sda6        56d170c7-6c0d-4710-ae68-cbb5d2a08a03   swap       
/dev/sda7        cb2d09c0-f168-4ce3-bda3-f5616b7280a1   ext4       koti

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/disk/by-uuid/8d01f754-262a-43b8-bfce-2cc6e97723d5 /                        ext4       (rw,relatime,user_xattr,acl,barrier=1,data=ordered)
/dev/sda7        /home                    ext4       (rw)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

```

---

### Post by bcbc on 2011-06-28
Have you tried this: [http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

> Method 3
Start the computer by using your Windows XP CD-ROM. Press any key to boot from the CD.
After the setup files are finished loading press R to repair using Recovery Console.
When you are in the recovery console, select the installation to log on to (usually number 1), and then press ENTER.
Login to the Administrator account by typing the password for this account, and then press ENTER.
At the recovery console command prompt, type the following command, and then press ENTER: 

For Uni-Processor systems:
expand <cd-drive>:\i386\ntoskrnl.ex_ <hd-drive>:\Windows\system32\ntoskrnl.exe
For Multi-Processor systems:
expand <cd-drive>:\i386\ntkrnlmp.ex_ <hd-drive>:\Windows\system32\ntoskrnl.exe
Note In these two commands, the <cd-drive> placeholder represents the drive letter of your CD drive, and the <hd-drive> placeholder represents the drive letter of the hard disk on which windows is installed.
If you receive a prompt to overwrite the file, press Y.
Type exit, and press ENTER at the command prompt.

Edit: this might also work: [http://www.ozzu.com/mswindows-forum/ntoskrnl-exe-corrupted-windows-wont-open-t24580.html#p71621](http://www.ozzu.com/mswindows-forum/ntoskrnl-exe-corrupted-windows-wont-open-t24580.html#p71621)


Also your bootinfoscript results look a bit strange: "/dev/sda1 already mounted or busy". Even though it probably is mounted, bootinfoscript doesn't seem to have a problem analyzing the mounted drives on my machine. (Maybe this is different running on Arch? but there could be some other issues).

---

### Post by Ramla on 2011-06-29
> **bcbc said:**
> Have you tried this: [http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

Edit: this might also work: [http://www.ozzu.com/mswindows-forum/ntoskrnl-exe-corrupted-windows-wont-open-t24580.html#p71621](http://www.ozzu.com/mswindows-forum/ntoskrnl-exe-corrupted-windows-wont-open-t24580.html#p71621)

It seems my WinXP media doesn't have a recovery console option, but I've before tried to copy the file from the media in linux with no success. Now I tried the XP option "Try the last known good configuration" which apparently fixes MBR and my XP booted fine. I installed the network drivers and downloaded graphics drivers after which I installed grub again only to see XP fail to boot with the ntoskrnl.exe corrupt or missing error.

> **bcbc said:**
> 
Also your bootinfoscript results look a bit strange: "/dev/sda1 already mounted or busy". Even though it probably is mounted, bootinfoscript doesn't seem to have a problem analyzing the mounted drives on my machine. (Maybe this is different running on Arch? but there could be some other issues).
I googled for some BIS results from arch users and found all of them report the failed mount except ones run on a live system. I'll be right back with the live kind of results.
...and here they are: ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => ISOhybrid (Syslinux 3.82-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       udf
    Boot sector type:  ISOhybrid (Syslinux 3.82-4.04)
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    41,945,714    41,945,652  83 Linux
/dev/sda2    *     41,945,715   104,888,384    62,942,670   7 NTFS / exFAT / HPFS
/dev/sda3         104,888,385 1,953,520,064 1,848,631,680   f W95 Extended (LBA)
/dev/sda5         104,888,448   314,616,959   209,728,512   6 FAT16
/dev/sda6         314,617,023   318,617,144     4,000,122  83 Linux
/dev/sda7         318,617,208 1,953,520,064 1,634,902,857  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
64 heads, 32 sectors/track, 3830 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0       346,111       346,112  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/sda1        8d01f754-262a-43b8-bfce-2cc6e97723d5   ext4       juuri
/dev/sda2        AA2C35482C3510B5                       ntfs       
/dev/sda6        56d170c7-6c0d-4710-ae68-cbb5d2a08a03   swap       
/dev/sda7        cb2d09c0-f168-4ce3-bda3-f5616b7280a1   ext4       koti
/dev/sdb1                                               udf        ARCH_201005

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /media/wtf               ext4       (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   1
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/8d01f754-262a-43b8-bfce-2cc6e97723d5 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/8d01f754-262a-43b8-bfce-2cc6e97723d5 ro
initrd /boot/kernel26-fallback.img

# (2) Windows
title Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0
UUID=56d170c7-6c0d-4710-ae68-cbb5d2a08a03 swap swap defaults 0 0
UUID=8d01f754-262a-43b8-bfce-2cc6e97723d5 / ext4 defaults 0 1
UUID=cb2d09c0-f168-4ce3-bda3-f5616b7280a1 /home ext4 defaults 0 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.492354870 = 13.413563904   boot/grub/menu.lst                             1
  18.404319286 = 19.761487360   boot/grub/stage2                               1
   2.680285931 = 2.877935104    boot/kernel26-fallback.img                     1
   2.251693249 = 2.417737216    boot/kernel26.img                              1
  18.634437084 = 20.008574464   boot/vmlinuz26                                 1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/vmlinuz26                                 1

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically
```

---

### Post by bcbc on 2011-06-29
Ramla, you have a problem with /dev/sda5. I'd start by fixing that. Everything else looks okay, near as I can tell.

---

### Post by Ramla on 2011-06-30
> **bcbc said:**
> Ramla, you have a problem with /dev/sda5. I'd start by fixing that. Everything else looks okay, near as I can tell.

It's an unformatted partition to be used with Windows once I get it to boot. Doesn't count as a problem.

---

### Post by bcbc on 2011-06-30
Searching around it appears this message can come from a whole bunch of things (even a bad keyboard/mouse, assuming the sources are accurate)

So it's best to eliminate grub. Have you confirmed that when you have a Windows bootloader, XP boots fine? And as soon as you install Grub you have this problem?
Obviously at some point XP was booting okay so I suppose you'll have to go through the steps and see what triggered the problem - maybe that will point to a possible solution.

Also run a complete chkdsk /r from a windows repair disk while you're at it.

---

### Post by Ramla on 2011-06-30
> **bcbc said:**
> Searching around it appears this message can come from a whole bunch of things (even a bad keyboard/mouse, assuming the sources are accurate)

So it's best to eliminate grub. Have you confirmed that when you have a Windows bootloader, XP boots fine? And as soon as you install Grub you have this problem?
Obviously at some point XP was booting okay so I suppose you'll have to go through the steps and see what triggered the problem - maybe that will point to a possible solution.

Also run a complete chkdsk /r from a windows repair disk while you're at it.

I do not have a Windows repair disk, and I cannot access the recovery console from my installation media, nor does automated system recovery work because I don't have some required diskette or a diskette drive. All I could do to fix windows' bootability was to select Last Known Good Configuration. I guess something might be up with the installation though, since that doesn't fix the MBR anymore.

However I would say that grub is at least the trigger here, since I could boot into Windows several times straight doing all kinds of driver installations, but only after installing grub back Windows fails to boot.

Maybe later I'll try another XP version, hopefully with a recovery console on the media, and see if anything changes.

---

