---
title: "Grub Issues - ( Path `/boot/grub' is not rea | error: failed to get canonica )"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by vixsandlee on 2013-03-02
Hello, I am having problems with grub, I will dump as much info as possible here, if someone could point me in the correct direction it would be great, because I really am running out of ideas :/

I put this in "Installation and Upgrades" because even though this is not a new install, I would guess grub issues most commonly fall into new installs


Thanks in advance.



```
xbmc@XBMC-PC:~$ uname -a
Linux XBMC-PC 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
xbmc@XBMC-PC:~$



```

```
xbmc@XBMC-PC:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.
xbmc@XBMC-PC:~$

```
```
xbmc@XBMC-PC:~$ sudo apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'grub' is not installed, so not removed
The following packages will be REMOVED
  grub-common* grub-emu* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
0 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
After this operation, 23.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134186 files and directories currently installed.)
Removing grub-emu ...
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub2-common ...
Removing grub-pc-bin ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
xbmc@XBMC-PC:~$

```
```

xbmc@XBMC-PC:~$ sudo apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  grub-gfxpayload-lists grub-pc-bin grub2-common os-prober
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common os-prober
0 upgraded, 6 newly installed, 0 to remove and 5 not upgraded.
Need to get 18.9 kB/2,387 kB of archives.
After this operation, 9,420 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ quantal/main os-prober amd64 1.56ubuntu1 [18.9 kB]
Fetched 18.9 kB in 0s (69.0 kB/s)
Preconfiguring packages ...
Selecting previously unselected package grub-common.
(Reading database ... 133625 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-pc-bin.
Unpacking grub-pc-bin (from .../grub-pc-bin_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.6_amd64.deb) ...
Selecting previously unselected package os-prober.
Unpacking os-prober (from .../os-prober_1.56ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/mysql.info.gz'
Setting up grub-common (2.00-7ubuntu11) ...
Setting up os-prober (1.56ubuntu1) ...
Processing triggers for ureadahead ...
Setting up grub2-common (2.00-7ubuntu11) ...
Setting up grub-pc-bin (2.00-7ubuntu11) ...
Setting up grub-gfxpayload-lists (0.6) ...
Setting up grub-pc (2.00-7ubuntu11) ...


Creating config file /etc/default/grub with new version
grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.
grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.
grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
xbmc@XBMC-PC:~$





```
```

xbmc@XBMC-PC:~$ sudo blkid
/dev/sda1: UUID="a6d540c2-1fff-4e92-a181-87a071d7e209" TYPE="ext4"
/dev/sda5: UUID="875363bd-347a-4c94-9af6-ed40e3c9459e" TYPE="swap"
/dev/sdb1: UUID="d344fe72-9c51-49b7-8280-b803b767ab30" TYPE="ext4"
/dev/sdc1: UUID="cb529aea-1449-4a4f-be86-3af66314bcc6" TYPE="ext4"
xbmc@XBMC-PC:~$

```

```

xbmc@XBMC-PC:~$ sudo fdisk -l
[sudo] password for xbmc:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023408


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1914451967   957224960   83  Linux
/dev/sda2      1914454014  1953523711    19534849    5  Extended
/dev/sda5      1914454016  1953523711    19534848   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b7e7ae6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    1  FAT12


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001becd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux
xbmc@XBMC-PC:~$

```

---

### Post by grahammechanical on 2013-03-02
First question: Where are you running the command sudo update-grub from? Is from XBMC on sda1? The command will look for [COLOR=#000000][FONT=Ubuntu Mono]/dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209 [SIZE=3] [SIZE=2]on the partition that you are running it from.[/SIZE]

Second question: How do you explain this difference

[/SIZE][/FONT][/COLOR]> /dev/sdb1              63   976768064   488384001    1  FAT12
[COLOR=#000000][FONT=Ubuntu Mono][SIZE=3]
[/SIZE][/FONT][/COLOR]> /dev/sdb1: UUID="d344fe72-9c51-49b7-8280-b803b767ab30" TYPE="ext4"
[COLOR=#000000][FONT=Ubuntu Mono][SIZE=3]
The same partition is described as having a FAT12 file system and also an ext4 file system. This may be a red herring. You may need to use this

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) It is the best that I can do for you . Regards.


[/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2013-03-02
We have seen issues with very large / (root) partitions. Grub gets lost when some of the boot files are near the start of the drive and some are beyond 100GB. There was a bug on drives over 500GB, but they said they fixed it, but we still see issues. 
Also is this a 32bit install?
Better to have a smaller / (root) and either separate /home or just data partition(s) with the new very large drives. I normally suggest 25GB with the larger drives.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by vixsandlee on 2013-03-03
Hmmm I never noticed the drive issues before (ext4 / FAT12) the drive was definitely done with ext4 because I only installed it a couple of months ago.

update-grub was being ran from sda1 so its not that.

I will have a look at boot-repair when I have a spare hour, the box does not have any GUI so I need to create a live USB to run it (I presume that wont be an issue ?) and see if that can solve it.

The install is x64.

Will see if boot repair solves it, I will also post the boot repair log so if anyone else has this problem atleast they may know what can fix it.


Thanks for the pointers.

---

### Post by oldfred on 2013-03-03
If partition table does not match format, Boot_repair will not fix that. 

From a gui you can use Disk Utility and change partition table id to be correct.

You can from command line use sfdisk to output partition table info and edit it then reimport it.
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdb > PTsdb.txt

see man sfdisk first:
 change sdb1 to type 83
sudo sfdisk --change-id /dev/sdb 1 83

---

### Post by vixsandlee on 2013-03-06
Urgh.

Ok.

I tried to reboot and it wouldn't boot after I had been messing about with grub (to be expected) so I used boot repair.


Before running boot repair.

[http://paste.ubuntu.com/5589875/](http://paste.ubuntu.com/5589875/)


After running Boot-repair

[http://paste.ubuntu.com/5589883/](http://paste.ubuntu.com/5589883/)

System now boots again (yay)
(I also fixed the id mismatch)


I still get this when running update-grub 

```

/usr/sbin/grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.

```


So its still messed up (even though it boots) as the system cant change anything with grub :/

hindsight is a great thing, but moving everything off the drive / re-formatting / re-installing with a seperate /home/ and / is really not something I wantr to do if it can be avoided :/

---

### Post by oldfred on 2013-03-06
That error seems to be typical with the too large / (root) partition. Try shrinking / to a much smaller size or make a small /boot at the beginning of the drive.

You do not have to reinstall, but will have to move some data around. For new users we often suggest the separate /home. But I prefer to have my /home inside / and all in a 25GB partition. With system files close together hard drive does not have to jump around so much. Then I create data partitions for all data and mount those partitions and link the folders back into /home, so it looks & acts like a standard install.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by vixsandlee on 2013-03-07
urgh, they should make sure this is noted during the installer on larger drives if this is the case.

I will have a look see and a play when I have the time.

thanks for the help it is really appreciated, hopefully if I shrink it the problem will be solved.

---

### Post by vixsandlee on 2013-03-07
sigh.

resized to under 500G

still the same

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023408


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   895965183   447981568   83  Linux
/dev/sda2      1914454014  1953523711    19534849    5  Extended
/dev/sda3       895965184  1914451967   509243392   83  Linux
/dev/sda5      1914454016  1953523711    19534848   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b7e7ae6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001   83  Linux


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001becd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux
xbmc@XBMC-PC:/etc/default$

```


```

sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.

```


going smaller is possible (obviously) but I really want to avoid it, because I have a lot of things configured to use the /home/ directory and I would have to mess about with all that (its also a HTPC with a TV tuner and needs loads of space for recordings in /home/ although that is easy to change)

It seems stunning to me that in todays world grub can go **** up and break on large hard disks! Its not even cost effective to buy under 500gig nowadays for most PC's especially not for HTPC's


EDIT //

Going to re-size it to under 100G and see if that fix's it.

Its going to take over 3 hours :(

---

### Post by oldfred on 2013-03-07
I do not have a HTPC, but I see a lot of users install Ubuntu to one smaller / system partition, and use a different format for the movie partition. Not sure if there are a lot of advantages but some have posted that before.  A couple recently used small SSD for boot and all data on rotating drive.

I link my data from a data partition on another drive and then link all the folders from that data partition into my /home. System mostly sees only the standard files structure but it really is links.

---

### Post by vixsandlee on 2013-03-07
Nope its still ^&^£%64!!!!!

```

xbmc@XBMC-PC:~$ cd /
xbmc@XBMC-PC:/$ sudo update-grub
[sudo] password for xbmc:
/usr/sbin/grub-probe: error: failed to get canonical path of /dev/disk/by-uuid/a6d540c2-1fff-4e92-a181-87a071d7e209.
xbmc@XBMC-PC:/$

```

```

xbmc@XBMC-PC:/$ sudo fdisk -l


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023408


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   166651903    83324928   83  Linux
/dev/sda2      1914454014  1953523711    19534849    5  Extended
/dev/sda3       166651904  1914449919   873899008   83  Linux
/dev/sda5      1914454016  1953523711    19534848   82  Linux swap / Solaris


Partition table entries are not in disk order

```


This is bloody frustrating :(

Well any other ideas I suppose ?

---

### Post by oldfred on 2013-03-07
Sometimes a full chroot uninstall grub & reinstall grub works or helps. You can do that from Boot-Repair.

Sometimes Supergrub will boot.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Then you can to the full reinstall of grub from inside your install.
      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

