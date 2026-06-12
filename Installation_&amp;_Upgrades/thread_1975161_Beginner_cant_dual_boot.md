---
title: "Beginner cant dual boot"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by Peter Wilson on 2012-05-07
Hi I'm new to Linux/Ubuntu and am strulggling.  I tried ubuntu 64 bit on an exterbal hard-drive and liked it so I decided to install alongside W7.  I had c: for windows, d: for docs, and a samsung recovery partition too.  When I tried to install alongside windows, ubuntu only gave me the choice of resizing the d: which i did and then installed ubuntu.  The pc then restarted, and went straight in to w7! no choice to boot ubuntu.

Why cant I load ubuntu even though it installed (properly I think).  I am happy to reinstall in someone can help me.  I want to keep W7 on c, d for docs (accessible in W7 and in ubuntu) and another partition for ubuntu.

Thanks very much in advance!

---

### Post by dgharmon on 2012-05-07
> **Peter Wilson said:**
> I tried ubuntu 64 bit on an exterbal hard-drive and liked it so I decided to install alongside W7

See this ... [ Changing location of Bootloader]("http://www.linuxformat.com/forums/viewtopic.php?t=760&view=previous&sid=bc480564ef68e834a7cbca134153942e")

---

### Post by kansasnoob on 2012-05-07
> **dgharmon said:**
> See this ... [ Changing location of Bootloader]("http://www.linuxformat.com/forums/viewtopic.php?t=760&view=previous&sid=bc480564ef68e834a7cbca134153942e")

Arrgh that's from 2005!!!!!!!!!!!!!

Horrible, horrible advice :-x

We first need to see what's installed where. I'd first want to see the output of this command from a live CD/USB:

```
sudo parted -l
```

---

### Post by jonnyboysmithy on 2012-05-07
Do you know what version of ubuntu you are using?

Ok, so what kansasnoob means is to open a terminal (push alt+f2 type gnome-terminal and hit enter) and in the terminal run this: 
```
sudo parted -l
```
And post on here what it says.

---

### Post by Peter Wilson on 2012-05-07
It is 12.04 64 bit. im on a samsung laptop i5 6 gb ram

---

### Post by Peter Wilson on 2012-05-07
open a terminal (push alt+f2 type gnome-terminal and hit enter) and in the terminal run this: 
 	Code:


how do i do this when i cant boot into ubuntu? u mean using my external hardrive again?

---

### Post by mips on 2012-05-07
> **Peter Wilson said:**
> 
how do i do this when i cant boot into ubuntu?

Use the ubuntu livecd you installed from.

Also paste the output of **sudo fdisk -l** here, where l is a lowercase L.


Towards the end of the ubuntu installation you did do you recall where you specified GRUB to be installed?

---

### Post by Peter Wilson on 2012-05-07
peter@peter-300E4A-300E5A-300E7A:~$ sudo parted -l
[sudo] password for peter: 
Model: ATA WDC WD7500BPVT-3 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   292GB  292GB   primary   ntfs
 3      292GB   728GB  436GB   extended                  lba
 5      292GB   699GB  407GB   logical   ntfs
 6      699GB   722GB  23.3GB  logical   ext4
 7      722GB   728GB  6350MB  logical   linux-swap(v1)
 4      728GB   750GB  21.7GB  primary   ntfs            diag


Model: WDC WD80 0VE-00HDT0 (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  80.0GB  80.0GB  primary  fat32

---

### Post by Peter Wilson on 2012-05-07
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe4b06cc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   570632191   285212672    7  HPFS/NTFS/exFAT
/dev/sda3       570634238  1422753791   426059777    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1422753792  1465147391    21196800   27  Hidden NTFS WinRE
/dev/sda5       570634240  1364819318   397092539+   7  HPFS/NTFS/exFAT
/dev/sda6      1364819968  1410349055    22764544   83  Linux
/dev/sda7      1410351104  1422753791     6201344   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 b

---

### Post by Peter Wilson on 2012-05-07
i just put the dvd back in and booted up....and this time the purple screen which lets me choose ubuntu/windows came up! so i am now in ubuntu installed on pc not live cd....

another strange thing dont know if this has any relevance...even tho usb hdd is at top of list in bios boot list....it wont boot into usb unless i do f2...bios boot order every time! i just go in....usb is at top of list...i save and then the usb loads! but wthout going into the bios every time it wont work!

anyway....how do i get this boot loader or whatever it is working?  thanks v much for ur help

---

### Post by anspectrum on 2012-05-07
> **Peter Wilson said:**
> Hi I'm new to Linux/Ubuntu and am strulggling.  I tried ubuntu 64 bit on an exterbal hard-drive and liked it so I decided to install alongside W7.  I had c: for windows, d: for docs, and a samsung recovery partition too.  When I tried to install alongside windows, ubuntu only gave me the choice of resizing the d: which i did and then installed ubuntu.  The pc then restarted, and went straight in to w7! no choice to boot ubuntu.

Why cant I load ubuntu even though it installed (properly I think).  I am happy to reinstall in someone can help me.  I want to keep W7 on c, d for docs (accessible in W7 and in ubuntu) and another partition for ubuntu.

Thanks very much in advance!


It is odd if you are facing this issue. Ive installed countless number of times Ubuntu with Windows or other way round (but arch was 32 bit). Follow this link step by step and hopefully you will succeed.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

:KS

---

### Post by oldfred on 2012-05-07
I would like to confirm where grub2 installed its boot loader. The MBR of sda or the MBR of your external drive?

download this into your liveCD or USB and post the results.txt it creates.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Peter Wilson on 2012-05-07
i am now logged in to the installed ubuntu....can i install this program u say here?

---

### Post by oldfred on 2012-05-07
It should work from any Ubuntu, installed, liveCD or USB and may work mostly in other Linux, but may need a app or two that may not be installed by default.

---

### Post by jonnyboysmithy on 2012-05-08
> **oldfred said:**
> It should work from any Ubuntu, installed, liveCD or USB and may work mostly in other Linux, but may need a app or two that may not be installed by default.
How about we give him the line of code so that he can install grub2 on all his disk, wouldn't that be easier/better?

---

### Post by Peter Wilson on 2012-05-08
I cant seem to sort this I the have messed things up even more now!  I have wiped ubuntu now and resized the d drive.  i now have 4 partitions....a 100mb samsung partition....a 200+gb c: with windows 7, a 400+ d: with docs and a 20gb recovery partitiion.

i want to install ubuntu and remove windows 7 from the pc on c:.  I tried to do that and was warned that it would delete all 4 partitions and use whole hardrive 750gb!  I dont want that! just on c:!

how do i do this?  i chose the 3rd option of sorting out partitions myself...after having read many help guides i think i get that i need to do the mount point / and to install the bootloader onto the main hardrive....but how do i choose to format and install only on one partition? just by highlighting it?! im scared i will loose all my docs and the recovery partitions!

please help////i really want ubuntu up and running today! its so fast!

---

### Post by jonnyboysmithy on 2012-05-08
Ok, first things first **Backup that data!!**

Seriously, **if something goes wrong your going to have a problem if the data is important **so really do a backup of the stuff you want before moving on. Just make a copy of the files you want onto an external harddrive or another computer. Its as simple as that. That will be a few minutes well spent.

---

### Post by mips on 2012-05-08
**Back up your data first!!!!**

Did you create DVD install media from your recovery partition? If you have not do that first so you have a hard backup of your recovery partition.

Once you have done the above you can format the entire drive and start from scratch if that is what you wanna do.

---

### Post by oldfred on 2012-05-08
Most standard Windows installs use all 4 primary partitions. You can convert one primary to an extended and have many logicals in the extended, but still have to delete one of the existing primary partitions to make the extended.

Windows usually uses 2, one hidden 100MB boot/repair and the main install or c: drive (really a partition). Vendors then do not give an install DVD, but just put an image of the drive in a partition, which you should use to make a set of DVDs to reinstall the system to as purchased (more if you ever want to sell later). And the vendors use a partition for some vendor tools. Usually that is small and easily backed up.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.

HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. fullcirclemagazine.org

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows or it may convert to dynamic partitions which do not work with Linux.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

