---
title: "Recovering data for a failed upgrade 12.04 - 14.04"
date: 2014-11-06
forum: Installation &amp; Upgrades
---

### Post by Stefano_Cardanobil on 2014-11-06
Hi,

I have messed up with my upgrade from 12.04 to 14.04 and I need help to fix it (I have some data I would like to recover).

This is the story, I would be really happy for any help!

1) I had a dual boot windows 7 / ubuntu 12.04 and I decided to upgrade
2) I backuped almost all data (not all of them because of some misunderstandings with my wife) on an USB
3) I forgot to throw out the USB and I started the upgrade
4) The first time, it complained about having to little hard-drive space (it must be noted that my Ubuntu partition only had 2 or 3 GB free space)
5) I deleted some old stuff, emptied the trash bin, planned in my mind to increase the ubuntu partition size and started the upgrade again. I forgot to expel the USB again
6) All went well until maybe two third of the installation. Then an error message appeared, whose header said something about not having enough space, but whose text body was unreadable (only squares to be seen). I could not do anything so I ignored it.
7) Alle seemed to go well until the end
8) When asked to rebooted, I rebooted and now
9a) If I let the USB in and boot, I can choose between Windows and Ubuntu. If I choose Ubuntu, it opens the menu with the kernel versions to choose from, but I can only choose *Ubuntu, then it complains about not finding something about init and enter initframs
9b) If I leave the USB out, it search for some init stuff and then freezes
10) I then booted with my Ubuntu 14.10 liveCD and checked whether I can image any partition and try to rescue the data. Using gparted only shows me the ntfs Windows partitions, but nothing else

I only need to recover the workspace directory of the eclipse installation, then I would be happy!

---

### Post by Bashing-om on 2014-11-06
Stefano_Cardanobil; Hello ; Welcome to the forum.

Houston, we 'may' have a problem . But, let's see what we can do for a solution.
This:
> 
10) I then booted with my Ubuntu 14.10 liveCD and checked whether I can image any partition and try to rescue the data. Using gparted only shows me the ntfs Windows partitions, but nothing else

indicates that this is a WUBI install ( ubuntu installed as a virtual file system within Windows).
Let's have a look and verify what is:
Boot the liveDVD to terminal and
Post back the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
df -h
df -i

```
which will relate the partitioning and disk space usage.


[INDENT][INDENT]thus a tale is told
[/INDENT][/INDENT]

---

### Post by Stefano_Cardanobil on 2014-11-07
Hi Bashing-om,

thank you for your friendly answer. Below the output of the commands you asked for

sudo fdisk -lu

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x84607c5a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2           206848 1932550143 1932343296 921.4G  7 HPFS/NTFS/exFAT
/dev/sda3       1932550144 1953521663   20971520    10G 27 Hidden NTFS WinRE


sudo parted -l

Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   989GB   989GB   primary  ntfs
 3      989GB   1000GB  10.7GB  primary  ntfs         diag


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: TSSTcorp CDDVDW SH-224DB (scsi)                                    
Disk /dev/sr0: 1163MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1152MB  1155MB  2327kB               EFI

df -h

Filesystem      Size  Used Avail Use% Mounted on
/cow            3.9G   65M  3.9G   2% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           793M  1.2M  791M   1% /run
/dev/sr0        1.1G  1.1G     0 100% /cdrom
/dev/loop0      1.1G  1.1G     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           3.9G  1.1M  3.9G   1% /tmp
none            5.0M  8.0K  5.0M   1% /run/lock
none            3.9G   76K  3.9G   1% /run/shm
none            100M   56K  100M   1% /run/user

df -i

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/cow           1013830    875 1012955    1% /
udev           1010872    557 1010315    1% /dev
tmpfs          1013830    608 1013222    1% /run
/dev/sr0             0      0       0     - /cdrom
/dev/loop0      190346 190346       0  100% /rofs
none           1013830      4 1013826    1% /sys/fs/cgroup
tmpfs          1013830     17 1013813    1% /tmp
none           1013830      3 1013827    1% /run/lock
none           1013830      4 1013826    1% /run/shm
none           1013830     30 1013800    1% /run/user

---

### Post by Bashing-om on 2014-11-07
Stefano_Cardanobil; Umphhh ..

Still, the tale is told that this is a WUBI install of ubuntu, as there is no indication of any partitions (ext4 family) devoted to linux.
Does the ubuntu install exist on the USB device:
> 
9a) If I let the USB in and boot, I can choose between Windows and Ubuntu. If I choose Ubuntu, it opens the menu with the kernel versions to choose from, but I can only choose *Ubuntu, then it complains about not finding something about init and enter initframs

That is not plugged in, such that it is not seen in the output ???

I have zero experience with WUBI, - If indeed we still look at WUBU - ( ubuntu installed on a USB drive ??) and no idea how one could access the virtual ubuntu file system.

Wait and see what others can advise to facilitate accessing ubuntu to retrieve your data.

[INDENT][INDENT]I just do not do
[INDENT][INDENT][INDENT][INDENT]Windows
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bcbc on 2014-11-07
If it's a Wubi install, you can just use [ext2read]("http://ext2read.blogspot.ca/") from Windows to open the file C:\ubuntu\disks\root.disk and copy whatever you want.

If it's a Wubi install, then upgrading to 14.04 will always stops it booting: [http://askubuntu.com/q/453411/14916](http://askubuntu.com/q/453411/14916)
You may have other issues with your install though, so that may not be the only fix you require.

I'd recomment you post the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") as this will explain a lot more about what is going on, in particular why you seem to need the USB to boot.
PS. Does Windows boot okay? You didn't say...

PPS. If Windows doesn't boot you can still mount the root.disk from the live cd (assuming it's really a Wubi install):
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp -r /mnt/home/<path to eclipse> /media/win/someplace
sudo umount /mnt
sudo umount /media/win

```
The above code mounts the windows partition, the Wubi root.disk, and then copies the eclipse folder off the root.disk to the windows partition. You'll have to identify where the eclipse folder is and where it's going on the Windows C: drive (in this case /media/win is equivalent to C:\)

---

### Post by Stefano_Cardanobil on 2014-11-07
Hi,

thank you, you saved my life! Great to get competent help! :p

>> If it's a Wubi install, you can just use [ext2read]("http://ext2read.blogspot.ca/") from Windows to open the file C:\ubuntu\disks\root.disk and copy whatever you want

It just worked and I was able to recover all eclipse classes I needed.

Last question: how can I clean up the mess now? Can I uninstall the wubi installation and install 14.10 just anew from the liveCD? Or what would you suggest?

To answer your questions: Windows does boot okay.

Thank you again
Stefano

---

### Post by Bashing-om on 2014-11-07
Stefano_Cardanobil; Hey hey !

Yep, no substitute for experience, huh ? Glad things are working out.

It being your system and you usage can not directly advise,
But, here is food for thought:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Of course, one could also delete the WUBI from within Windows and do a clean fresh install of ubuntu as a true dual boot.


[INDENT]many paths 
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bcbc on 2014-11-07
I didn't find 14.10 very stable. Graphics seemed off, with phantom window/mouse trails. That could just be my hardware, but I'd recommend you use 14.04.1.

I assume you're talking about doing a normal dual boot, because Wubi doesn't work properly for these releases. If you are still considering Wubi try that askubuntu fix I linked to in my previous post on your current install first and note that both the 14.04.1 and 14.10 wubi.exe's don't work properly. The first requires a [manual]("http://askubuntu.com/a/540034/14916") workaround to install, but the second [requires a rebuilt Wubi]("https://bugs.launchpad.net/wubi/+bug/1385930").

If you do get your current install working then that migration script mentioned is an option. Otherwise, it's not.

---

### Post by Stefano_Cardanobil on 2014-11-08
Ok, I would not mind actually installing everything completelz from scratch since I saved all my data. Only I dont know how to wipe out the wubi install thouroughly.

---

### Post by bcbc on 2014-11-08
To uninstall Wubi, you can go to Add/Remove programs (in Control Panel) and double click on "Ubuntu". This will completely delete the install.

---

