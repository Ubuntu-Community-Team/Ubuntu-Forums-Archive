---
title: "Install multiple distros on SSD hints?"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by westender on 2010-12-15
Hey all,
 
I dual booted Karmic on my old laptop. I just received my new machine, Envy 17 with a 160 GB SSD and a 640 GB hard drive with Windows 7 pre-installed. I want to multiboot Windows, Maverick and the CAElinux distro, on the SSD I am thinking. I am in the process of searching the forums in regards to partitioning strategies and hints to smooth the installs. If anybody has any tips it would be much appreciated.
 
 
Peace,
Mike

---

### Post by tommcd on 2010-12-15
Here is a discussion on journaling file systems (ext3 and ext4) for SSD drives from a linux kernel programmer:
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
The bottom line is that it is ok to use ext3 or ext4 on SSD drives. He recommends adding the **noatime** boot option to your */etc/fstab* file to reduce the extra cost of the journaling file system to the drive.
As for partitioning, I use a separate root partition for each distro that includes the home directory. I then use a /data directory for my data that all 3 of my linux distros share. This way the configuration files in home are kept separated on each distro's root partition and do not conflict with each other.

You may also want to go without a swap partition on the SSD, especially if you have at least 1-2GB memory.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by westender on 2010-12-15
OK, I went to install from a CD and when the process got to the "Allocate Drive Space" it did not recognize Windows 7 and was going to use ALL of my 160 GB SSD.  Trying to figure out how the drives are partitioned and what my next move is.

Here is my RESULTS.txt:

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   266,180,607   265,771,008   7 HPFS/NTFS
/dev/sda3         266,180,608   312,369,151    46,188,544   7 HPFS/NTFS
/dev/sda4         312,369,152   312,579,759       210,608   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18381F07381EE392                       ntfs       SYSTEM                        
/dev/sda2        9A0C3CBB0C3C93EB                       ntfs       OS                            
/dev/sda3        884091064090FBDE                       ntfs       RECOVERY                      
/dev/sda4        4467-13F7                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1410138310136ACE                       ntfs       DATA                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/HP_TOOLS          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

---

### Post by oldfred on 2010-12-15
You have used all 4 primary partitions as primary. You have to delete one primary and convert it to the extended partition to hold all the new logical partitions you want. 

Be sure to back up everything you want. If your system lets you write the recovery DVD which will probably only create a new image of the drive as purchased. Also it it lets you create a win7 repair CD. You may need that to repair windows and to run chkdsk if system does not boot at all.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by westender on 2010-12-16
Thanks for the info, the machine is brand new and I have the recovery disk so if I muck it up it won't be too painful.
 
It looks like I will want to delete the sda4 (HP_TOOLS) and create a new extended partition and resize sda2, does that sound right?

---

### Post by oldfred on 2010-12-16
Make a good backup of the tools partition. If you want you can create a new logical partition and copy the tools back into a logical.

Some HP only let you make one DVD recovery disk. Then you have to purchase another even if the first just did not work.

You may need a windows repair CD. It pays to have it as when you do need it of course if is difficult to get. There are available copies on the Internet.

---

### Post by tommcd on 2010-12-16
> **westender said:**
> 
It looks like I will want to delete the sda4 (HP_TOOLS) and create a new extended partition and resize sda2, does that sound right?
Your /dev/sda4 is not contiguous with /dev/sda2, so if you want to be able to make one large block of unallocated space for Ubuntu, you would need to delete /dev/sda4 and then shrink /dev/sda3 from the end of /dev/sda3. This will create one large block of unallocated space.

If you want two partitions for root and home, then yes, you could delete /dev/sda4 and the create a home partition there when you install Ubuntu. And shrinking /dev/sda2 will allow you to create a root partition in that space.

---

### Post by westender on 2010-12-22
Thanks for the help.  I have the recovery disk.  Still have a couple of questions:
 
Is there a big performance improvement if I install Ubuntu to the SSD as opposed to the HD?
 
I have read that I should use the Windows tool to resize the W7 partitions, is this accurate or can I safely use GParted?
 
Since I have the recovery disk can I delete the recovery partition?
 
What about the HP_TOOLS partition, can I move that to the HD or can I/should I create a logical partition in the Windows primary and put it there?
 
Again, thanks for everyone's help, I will have more questions.
 
Peace,
Mike

---

### Post by oldfred on 2010-12-22
We do not know what version of gparted you may have, so we normally suggest using windows tools to modify the windows partition, but not to create any new partitions for Linux as that may cause other problems. The newest gparted should be ok, but always reboot windows several times as it will want to run chkdsk after a resize. Do the windows reboots before doing anything else after the windows resize.

Some with SSD brag about 10 to 20 sec boot times where the rest of us have just under a minute depending on your hardware.

If your recovery partition lets you create a repair CD you should do that. If you have problems with windows, you can often repair it rather than do the total erase & reinstall that the recovery disk does. It is my understanding that HP only lets you create one recovery DVD, if that does not work then you have to purchase one from them. So I do not think recovery has much purpose, now. Even then, will you want to totally erase hard drive and restore it to the way it was the day you bought it? All updates and new software would have to be reinstalled and your data copied from your backup.

Are there things you use in the HP tools partition. It is usually small and after you create the extended partition you can create a small partition to copy the tools back, if you want them. Or just keep a good backup so you can reinstall if you need them in the future.

---

### Post by westender on 2010-12-26
Ok, my install went great!  No problems, just took my time and made multiple backups, for redundancy.  My partitioning probably leaves something to be desired but it works.

Now I just need to customize everything to my liking.  

Thanks for all the help!

Mike

Ubuntu 10.10 + Windows 7
Hp Envy 17
i7-720QM
8GB DDR3
17.3" 1920 x 1080 display
1GB ATI Radeon HD5850
160 GB SSD
640 GB 7200RPM HD
Blu-Ray ROM w/ SuperMulti DVD RW Double Layer


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

```

---

### Post by oldfred on 2010-12-26
Glad it is working. 

For future reference, since you mentioned you may be interested in multiple installs.

I had just windows & root & swap for Ubuntu for several years. I quickly added a NTFS shared partition, so I could have the same bookmarks and emails by sharing Firefox & Thunderbird profiles.

But now that I am in Ubuntu almost all the time, prefer clean installs, and multiple root partitions so I keep my old install while converting to the new install and then another root or two for testing. I then find a /data partition is worthwhile as I can then mount that into each install and have the same data like I do with my shared NTFS partition. I still have not converted the Firefox & Thunderbird from the NTFS to my /Data, but do not use my XP enough that it matters.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by westender on 2010-12-26
I re-partitioned the HD, sdb, into an NTFS and an ext4, where I put /home.  I figure I can put anything that I want accessible to any system in the NFTS.  I, too, see spending the vast majority of my time in Ubuntu so I might change things up.  All-in-all things are running smooth, still tweaking my desktop and things.

Peace,
Mike

---

### Post by efflandt on 2010-12-26
If your SSD supports TRIM and you are using ext4 file system with 2.6.33 or newer kernel, you can enable TRIM in Linux using discard option in /etc/fstab.  Although, I disabled the ext4 journal using **sudo tune2fs -O ^has_journal /dev/sdb1** (the option is capital -O, substitute your SSD partition for /dev/sdb1).  My PC is on a UPS, but even without that, power failure or system lockup never caused me any problems long before Linux had journaling.

If you have enough RAM, you can also use tmpfs for /tmp (like iso on USB does).

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e70810eb-379d-4f9f-9087-54c2f1cd96f9 /    ext4    noatime,discard,errors=remount-ro 0       1
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0
```

---

