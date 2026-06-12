---
title: "Dual Boot problem - Grub Rescue and failed mounting"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by Loose Hand Luke on 2011-06-22
Hi all,
I'll start by warning you I'm totally new to all this.

I wanted to use Ubuntu for web browsing, word processing, charts and graphs etc etc, but still wanted windows for gaming.

A friend of mine set up my pc to dual boot Ubuntu 9.10 and windows XP 64bit.

Its one HD, with 3 partitions:
- Lynux
- Windows
- Data

Its worked fine for ages and I've not re-installed anything, just used it.
Then one day it failed to boot Ubuntu after I'd selected it on the boot list, but once I rebooted it was fine again.
Then the other day it failed again and upon restart I got the "Grub Rescue>" prompt.

I did the obligatory "Google" and thought it might be a grub problem.

I booted from the install CD and tried:

[I]ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)[/I]

So have I got "Grub2" ???

Screen used to look like this (ish):
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png[/IMG]
(borrowed from Ubuntu help site)

So I did:

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86d5f01c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       27791   172032052+   f  W95 Ext'd (LBA)
/dev/sda3           27792       30401    20964825   83  Linux
/dev/sda5            6375       27791   172032021    7  HPFS/NTFS
[/I]

And also tried the Boot info script route which said that sda3 was the Ubuntu partition and the problem was - 

"Mounting failed:   mount: unknown filesystem type ''


Here's the list

```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 446737599 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 256 for /boot/grub.
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86d5f01c

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda2         102,398,310   446,462,414   344,064,105   f W95 Extended (LBA)
/dev/sda5         102,398,373   446,462,414   344,064,042   7 NTFS / exFAT / HPFS
/dev/sda3         446,462,415   488,392,064    41,929,650  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3C1C597B1C5930DE                       ntfs       
/dev/sda5        5084BC7684BC5FE0                       ntfs       data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer 
--------------------------------------------------------------------------------


```When I click **places/Homefolder/** and look at my list of directories and HD's on the left, I can see the other two partitions, Windows and Data.
The 3rd has a HD symbol and is called File System.
I can open it and it brings up a window labelled: *"/"* and seems to contain Ubuntu folders, but its none of the important contents tie up with what I've found on the help forums.

I also tried to go through an install process using the CD, and the Lynux partition was listed as "Not formatted" so I backed out of the install in case I ruined anything.

So I'm now lost. I don't know what to do about it. I've got data on the ubuntu partition that I'd like to save so don't want to just format and start again!
](*,)

Thanks guys.

---

### Post by Loose Hand Luke on 2011-06-22
Tried some more fiddling but can't work out why it won't mount or allow me to select operating systems on boot up :confused:

---

### Post by oldfred on 2011-06-22
The boot script list from partition table shows sda3 as Linux. But in trying to look at partition it gives an error. 

Your grub menu was typical of a grub legacy install with part upgraded to grub2. It was for testing of grub2 and if it worked you could then complete the upgrade to grub2. You now have grub2 in the MBR, but without the script mounting sda3 we cannot see if it is complete or not.

Try this from liveCD:

From liveCD so everything is unmounted,swap off if necessary, change sda3 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda3
if errors:
sudo e2fsck -f -y -v /dev/sda3

---

### Post by Loose Hand Luke on 2011-06-23
Thank you for the help Oldfred,
This is what came up:

[I]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3
/dev/sda3: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/I]


So I did your second option and after a bunch of check and errors, it gave a list of fixings followed by this:

[I]/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****

  315145 inodes used (24.04%)
     141 non-contiguous files (0.0%)
     435 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 281144/118
 1593882 blocks used (30.41%)
       0 bad blocks
       1 large file

  230115 regular files
   42909 directories
      68 character device files
      26 block device files
       0 fifos
     527 links
   42014 symbolic links (33775 fast symbolic links)
       4 sockets
--------
  315663 files
ubuntu@ubuntu:~$[/I]


So will try a reboot and see if that's helped. :D

---

### Post by Loose Hand Luke on 2011-06-23
IT LIVES!

Thank you so much for the help Oldfred! All seems spot on again! :KS

Would you mind telling me, in simple terms if possible, what that command I typed in actually did?
I'm still learning :)

Also, you mentioned upgrading to Grub2, is it worth me doing that?

Once again, thanks for the help!

---

### Post by varunendra on 2011-06-23
> **Loose Hand Luke said:**
> IT LIVES!

Thank you so much for the help Oldfred! All seems spot on again! :KS

Would you mind telling me, in simple terms if possible, what that command I typed in actually did?
I'm still learning :)

Also, you mentioned upgrading to Grub2, is it worth me doing that?

Once again, thanks for the help!

Mmmm.. actually I'm posting just to keep record of this thread as we sometimes miss the most obvious solutions to simple problems like this!

About your question -
the last command obviously fixed the errors based on scan results (like chkdisk does in XP)! Perhaps it rebuilt the 'superblock'.
Maybe oldfred can give a precise explanation.

Since you are using Karmik (9.10), I think you should upgrade to Grub2. But you don't need to do so if your current setup is working and you want to just stick with it. Newer versions may refuse to work with Grub legacy. But then again, they'll automatically install Grub2 when you install them!

So in short - don't bother if your current setup is working!

@oldfred,
Sorry for interfering, I just couldn't resist! :)
Curiously awaiting your response to the OP's last questions..

---

### Post by mue.de on 2011-06-23
Hello,

just an idea to look at:
i found a good article (in german) at: ubuntuusers.de, Title 'GRUB2 - Reparatur', which was the solution for me, as i had a similar problem.
I did an 'sudo update-grub', booted with an Ubuntu 10.10 Live-DVD.

Sorry for my english

mue.de

---

### Post by oldfred on 2011-06-23
+1 on varunendra comments.

I just know that if file structure is somehow broken the fsck will try to fix it, just like chkdsk does in windows. It is part of the advantage of a journaled system that it is more repairable. There are also backup superblocks and some times you have to use those or use testdisk.

---

### Post by Loose Hand Luke on 2011-06-23
Awesome! Thank you so much everyone for the help!
Very much appreciated :D

---

