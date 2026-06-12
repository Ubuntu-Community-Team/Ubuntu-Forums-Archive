---
title: "Missing Operating System"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by atmega-ist on 2010-05-01
Hello, all -

I've been looking through the forum and have found a few threads on this subject but haven't had any luck with the proposed solutions in those posts.

The version I used was at the end of a fairly straightforward [path]("http://www.ubuntu.com/getubuntu/download") so I assume it's something on my end rather than Ubuntu itself.  I seem to have completed the installation successfully but when I remove the disk after install and set my boot order back to default I get the (what seems to be famous) message: "Missing operating system".  Running from the CD, however, works fine.

I've been reading about the Master Boot Record and am suspecting that has something to do with it but will admit that most of it (Wikipedia) is over my head when it comes to applying it to my situation.

This install is mostly for exploratory purposes and there's no data on the machine in question so if any suggestions are made easier by formatting, reinstalling, etc...  don't hesitate to say so.

Thanks a lot!

---

### Post by bcbc on 2010-05-01
You probably just need to install grub2 to the disk MBR. See this post for details...[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Do what it says for 9.10 - this also works for 10.04

---

### Post by koanhead on 2010-05-01
Well, if you won't hurt anything by reinstalling, you may as well try it. If you are curious, try booting from the cd and choose the "boot from first hard drive" option. It sounds as though the install may have gone off ok, but for whatever reason grub (the bootloader) was not installed correctly. Maybe the installer put it somewhere incorrect or maybe it is corrupt. Who knows?
If you can boot into the installed system by doing that, then you can maybe rescue the installed system by reinstalling grub. There are some useful utilities on the livecd which aren't installed by default, so it might be better to work from it. 
Of course, the easiest way to go would be to just go ahead and reinstall, and see if that works.

---

### Post by wilee-nilee on 2010-05-01
post this boot script, in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by atmega-ist on 2010-05-01
bcbc -

thanks for the link.  everything went fine until the

```
sudo mount /dev/sda1 /media/sda1
```

the error returned states:

"mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error  In some cases useful info is found in syslog - try dmesg | tail or so"

is there anything I can do from here?

koanhead -

the reinstall produced the same results.  I should have been more clear in my original post that I had already tried but was curious to know if there were alternate install configurations.  thanks for the response, though

wilee-nilee -

downloaded the file but i don't have the ubuntu machine connected to the internet (and can't connect it at the moment).  also, i never really caught on to the whole flash-drive thing so i put it on a cd but can't see the cd drive from ubuntu...  just can't seem to win this one...  but the cd drive would be under "Places" on the top bar, right?

thanks a TON to all who replied

---

### Post by wilee-nilee on 2010-05-01
What I will say is chances are this script will be what saves the installs. You will have to figure out how to do it.

---

### Post by atmega-ist on 2010-05-01
wilee -  i'll be sure to see if i can find a flash drive and get that posted.  in the meantime, i noticed that when i try to reinstall, the partition step says that there's no OS installed (after it had just sat there 10 min before that and crawled through an installation...)

I noticed on another post (of course i can't find it again) that i need to create 3 partitions - "/", "/boot" and "swap".  i can't seem to get it to let me create more than one partition, though...  could this be contributing to the problem?  how does one create multiple partitions in the install wizard?

thanks

---

### Post by atmega-ist on 2010-05-01
wilee-nilee -

Here's the boot info.

Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,155,279    78,155,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2096 MB, 2096627712 bytes
40 heads, 39 sectors/track, 2624 cylinders, total 4094976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  64     4,094,975     4,094,912   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c93123fa-bc05-4d94-8316-e38165f1e8cc   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14D5-485C                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/14D5-485C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

```

---

