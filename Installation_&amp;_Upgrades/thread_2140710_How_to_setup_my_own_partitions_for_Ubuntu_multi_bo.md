---
title: "How to setup my own partitions for Ubuntu multi boot installation?"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by agrayray on 2013-04-30
I am having a hard time figuring out how to partion my multi-boot machine.

I currently have a dual boot win7+ubuntu12.04 on my machine.
I wanted to increase my swap size to 16GB (which is the RAM I have)
and also create some new partitions to install the 13.04 series:

Ubuntu 13.04 Desktop
LUbuntu 13.04 Desktop
XUbuntu 13.04 Desktop

I lowered the size of my windows partition and also my Ubuntu 12.04 partition.

What I want basically is to have:

16GB swap
and 10GB Ubuntu partitions.

When I resized the old partitions I got multiple free space entries that essentially I want to add to swap (dev/sda5 swap).
and create two new 1024 MB partitions for my Ubuntu installations.

Specifically I currently have the following in my partition screen:

[HTML]<pre>
Device        Type    MountPoint    Format?    Size    Used    System
dev/sda
dev/sda1    ntfs                471453    62444    Windows 7 (loader)
free space                        8912            
dev/sda6    ext4                1024    7694    Ubuntu 12.04.02 LTS (12.04)
free space                        8627        
dev/sda5    swap                897    0


</pre>[/HTML][FONT=courier new]
[/FONT]



1. I tried increasing the old swap (sda5) but the + is grayed out and if I type in 16384 it doesnt change.
2. I tried creating a new etx4 partition but when I clicked "install now" , I got error saying 'No root drive selected'

Can someone advise on what I need to do step by step please..I can not seem to figure what I need do :(

Questions
1. How to have just one sda5/swap of 16GB that will be used by all the Ubuntu partitions?
2. How to select the root or partition to install my new ubuntu installations into to get past the no root message?

THANKS IN ADVANCE!

---

### Post by oldfred on 2013-04-30
The only reason to have swap equal to RAM is if you hibernate. But if multi-booting hibernating is not recommended and you then cannot use the same swap as each system using swap, writes data into it.
But with that much RAM you will probably never use swap. I only have 4GB and am not sure I have ever used swap. My system with only 1.5GB only occasionally uses swap (turns gray for a second as swap is really slow compared to RAM). Just to have some swap 2GB is plenty with your RAM.

You have several choices. 
You can install each in separate partitions which will let you more easily delete. 
Or you can just install each desktop into one. And choose as you log in.
Or you can use virtual installs, so you are running each at the same time. With the RAM you have virtual may be a good choice. I have always dual booted, but many with extra RAM use virtual installs.

If multi-booting you may want separate data partition(s). I have two, one NTFS for sharing data with Windows and one Linux formatted for all new data as now I am not booting XP anymore. Then all the data can easily be accessed from every install.

Are you using gparted from live flash drive installer or gparted liveCD?

---

### Post by agrayray on 2013-04-30
Thanks for the reply..actually I do have a reason for that much swap... vmware Workstation (virtualization)

When I start my virtual machines in workstation I get warnings that say i should as much swap as the memory for that machine..and its aggregated..for example if I have one VM open that using 1GB and start another is using 512MB...I get a warning that vmware recommends increasing the swap to at least 1.5GB...and..I noticed a huge drop in performance running them now..(infact my whole machine was practically frozen)...

I never hibernate my machine...and this actually is just from the installation of Ubuntu 13.04 (not using gparted etc...)...I choose the "something else" option from the installation which takes you to a screen where you can edit your partitions.

I actually just got past the "No root drive selected error" from this link:
[http://askubuntu.com/questions/135705/no-root-file-system-is-defined-error-during-installation](http://askubuntu.com/questions/135705/no-root-file-system-is-defined-error-during-installation)
which simply was to put a forward slash in the mount settings for one of the partitions.

But I still can not figure out how to combine those free space sections and extended my swap partition...?

How does each ubuntu installation know what swap is available to it?  Can I just change those free space sections to swap to have the total I need or do I do need to change the size of the swap sda5?

---

### Post by oldfred on 2013-04-30
I somehow ended up with a couple of swaps and normally put one on each drive. A new auto install finds all of them and adds them to fstab. Not sure how that works. Still may be better to have one larger one.

Post screen shot of gparted. Use advanced editor and then you have a paperclip icon to attach screen shots.
And/or post this as it shows details, but picture is easily to see overall:

       sudo parted /dev/sda unit s print

---

### Post by agrayray on 2013-04-30
Thanks again for the reply..per you request (and thanks for mentioning fstab..i remember a little about reading that a few years ago :) )..here's a full dump of everything that I think could be useful..the parted command is the last one...

**rei@rei-ThinkPad-W530:~$ cat /etc/fstab**
#/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=9a907335-f47a-4c84-9943-cbac2f4d9922 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e08f0de2-beed-4d07-8090-2576bd15bbe4 none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=b807d534-6e09-4c03-a108-ce18c12d35a0 none            swap    sw              0       0
[B]


rei@rei-ThinkPad-W530:~$ sudo fdisk -l[/B]

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51a9e747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   920808688   460403320+   7  HPFS/NTFS/exFAT
/dev/sda2       920809470   976773165    27981848    5  Extended
/dev/sda5       975075328   976773165      848919   82  Linux swap / Solaris
/dev/sda6       938215424   958215423    10000000   83  Linux
/dev/sda7       920809472   938213768     8702148+  83  Linux
/dev/sda8       958216192   975065087     8424448   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3906963455  1953480704    7  HPFS/NTFS/exFAT
[B]


rei@rei-ThinkPad-W530:~$ sudo parted /dev/sda unit s print [/B]
Model: ATA TOSHIBA MK5061GS (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       920808688s  920806641s  primary   ntfs            boot
 2      920809470s  976773165s  55963696s   extended
 7      920809472s  938213768s  17404297s   logical   ext4
 6      938215424s  958215423s  20000000s   logical   ext4
 8      958216192s  975065087s  16848896s   logical   linux-swap(v1)
 5      975075328s  976773165s  1697838s    logical   linux-swap(v1)

as you can see..I went ahead and created the new 13.04 installation and changing the free space to swap..and as you said...Ubuntu already picked it up...that said...because I am still planning on installing other instances and partitions..I guess I need to add somethings to other /etc/fstab ([perhaps more config) to get my previous installation to recognize the new swap or what?  (Will test this out shortly)...also if it is better to use one large section for the swap (and assuming I can change it later using gparted)...how to get the machines to recognize the new partition setup?

---

### Post by oldfred on 2013-04-30
If you change partitions around you have to find the new UUID and create  entires in fstab or change the UUID if an old one was obsoleted.

If you have data partitions and want to mount with good permissions. Examples to copy & paste into fstab and edit for your UUID and mount point.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by agrayray on 2013-05-02
yes I noticed this after I added antother partition, for ex the windows drive disappeared from the ohter installations...anyway..I found my answer..the simple of it is..to use gparted..and more precisely to setup for anyone in the future..the way to do this is:

1. always click the try the installation first, this will give you a chance to connect to internet and install gparted if its not there
2. run gparted and decrease the size of the existing partitions, this will give you a free space entry
3. double click on the free space section and add the partition (for other new ubuntu installations choose ext as the file system (ext4 preffrd) and enter a '/' in the mount entry, for swap, simply select swap
4. repeat step 3 of just clicking on the free space until you have the partitions you want
5. select the partition you want to install ubuntu into and choose install

---

