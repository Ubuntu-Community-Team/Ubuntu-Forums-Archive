---
title: "grub configuring problem for dual boot system using RAID1"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by alidm on 2008-11-18
My desktop computer uses RAID1 (Mirror). I had a working copy of Microsoft Windows XP on it, but I wanted to install kubuntu 8.10 as well. So, I booted my system using kubuntu 8.10 CD, and then installed "dmraid" package. Afterwards I tried to go through the basic steps of installing kubuntu, but ubiquity crashed while trying to configure grub. So once again I booted the system on CD and tried to configure the grub directory manually this time. I followed the instructions on [[COLOR="Red"]this page[/COLOR]]("https://help.ubuntu.com/community/FakeRaidHowto") to have my grub configured. Then I could boot my system using this newly configured grub, and now everything works fine with my young Ibex! Though my only concern is that I'm not sure how to configure menu.lst to add my pre-existing copy of Windows to the boot list as well.
This is the content of my menu.lst at the moment:

```

title		Ubuntu 8.10, kernel 2.6.25-2-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.25-2-386 root=/dev/mapper/isw_dfafghhggg_ARRAY2 ro quiet splash 
initrd		/boot/initrd.img-2.6.25-2-386

#title		Ubuntu 8.10, kernel 2.6.25-2-386 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.25-2-386 root=/dev/mapper/isw_dfafghhggg_ARRAY2 ro  single
#initrd		/boot/initrd.img-2.6.25-2-386

#title		Ubuntu 8.10, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin

title		Microsoft Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

If I choose Microsoft Windows XP from the list, it gives me an error. Any help would be greatly appreciated.

Thanks,
--Ali

---

### Post by caljohnsmith on 2008-11-18
How about first posting the output of:
```
sudo fdisk -lu
```
Next, on start up when you get the Grub menu, press "c" to go to the Grub command line, and type the following without pressing enter:
```
grub> geometry (hd
```
And then press TAB for tab-completion; that should show your drives as (hd0), (hd1), (hd2), etc. Then for each drive do:
```
grub> geometry (hdX)
```
And based on what Grub reports as the size of the drive and the partition structure, try to determine which drive has your Windows on it, and let me know which one it is. Note that Grub will report the Windows partition as type "0x7". We can work from there if you want. :)

---

### Post by alidm on 2008-11-18
Thanks for the reply!

I did

```

fdisk -lu

```

in the terminal, and got this result:

```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1919db90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    82750814    41375376    7  HPFS/NTFS
/dev/sda2        82750815   165694409    41471797+  83  Linux
/dev/sda3   *   165694410   488263544   161284567+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1919db90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    82750814    41375376    7  HPFS/NTFS
/dev/sdb2        82750815   165694409    41471797+  83  Linux
/dev/sdb3   *   165694410   488263544   161284567+   7  HPFS/NTFS


```

I followed your instructions on the boot menu, and received these outputs:

On pressing tab at the end of command 

```

geometry (hd

```

I just got this command completed as

```

geometry (hd0,

```

and pressing an extra tab resulted in:

```

geometry (hd0,
Possible partitions are:
	Partition num: 0, Filesystem type unknown, partition type 0x7
	Partition num: 1, Filesystem type is ext2fs, partition type 0x83
	Partition num: 2, Filesystem type unknown, partition type 0x7

```

And when I did

```

geometry (hd0)

```

I received:

```

drive 0x80: C/H/S = 1023/255/63, The number of sectors = 488275968, LBA
	Partition num: 0, Filesystem type unknown, partition type 0x7
	Partition num: 1, Filesystem type is ext2fs, partition type 0x83
	Partition num: 2, Filesystem type unknown, partition type 0x7

```

commands (hd0,0), (hd0,1), (hd0,2), ... also responded the same thing.

And by the way, when I tried:

```

geometry(hd1)

```

I got this error message:

```

Error 21: Selected disk does not exist

```

Thanks again

---

### Post by caljohnsmith on 2008-11-18
OK, that's great, looks like your problem should be easy to solve; just replace your existing Windows entry in your menu.lst with:
```
title Windows XP
root (hd0,2)
chainloader +1
```
And let me know how it goes, or if for some reason that doesn't work. :)

---

### Post by alidm on 2008-11-19
So I did the change, and when I rebooted the system and chose Widows to boot up, grub hanged on "Starting up..."

---

### Post by caljohnsmith on 2008-11-19
Having it hang on "Starting Up..." is actually a Windows problem and not a Grub problem, so at least you are definitely booting the right partition now. Usually that Windows error is the result of the file system parameters being corrupted in the Windows boot sector, and fortunately "testdisk" can usually repair that problem; hopefully your RAID setup will not be an issue with testdisk. 

To use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you try and boot Windows from Grub.

---

### Post by alidm on 2008-11-19
I went through the steps you specified in your previous post and when I chose my Windows partition from the testdisk menu and selected "boot", I received this report:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  5150 254 63   82750752 [System Disk]

Boot sector
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

and when I went into "Rebuild BS", I got this report:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  5150 254 63   82750752 [System Disk]

filesystem size           82750752
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               16
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```

I quited and rebooted the system, though again it hanged on "Starting up..." when I tried to boot it up on Windows.

Thanks

---

### Post by caljohnsmith on 2008-11-19
I think you might have chosen the wrong partition; it looks like you chose the first partition, not the third partition which has your Windows install. Also, when you select the third partition, when you do the "Rebuild BS", if testdisk says that the backup boot sector is "bad" do not choose write. Only if testdisk says the backup boot sector is OK, then go ahead and choose "write". Let me know how it goes.

---

### Post by alidm on 2008-11-19
Yes, I had mistakenly chosen the first partition, so I went into the third partition and did the same. The backup boot sector was OK, so I went ahead and chose "write", then booted the system and received the same crap again. :(

---

### Post by caljohnsmith on 2008-11-19
That's not a good sign; Windows still hangs on "Starting up..."? If so, I would boot your Windows Install CD, go to the "recovery console" and run:
```
map
```
That will show the drive letters of your two NTFS partitions, and probably Windows will be "D", but change it in the following command if necessary:
```
chkdsk /r D:
```
And run it as many times as it takes until it reports no errors. If you don't have your Windows Install CD, you can download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Let me know if running chkdsk on the Windows partition makes any difference when you try and boot it again.

---

### Post by alidm on 2008-11-27
I tried to follow what you told. I booted my computer with the CD. It started detecting my hardwares, though after a while it suddenly gave me a blue screen containing this error message:

```

A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated.
Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical Information:

*** STOP: 0x0000007B (0xF78DA63C, 0xC0000034, 0x00000000, 0x00000000)

```

I thought it might be due to some problems with the CD. So I tried to boot my PC with another Windows CD that I was sure it works, and again I got the same message. I think there might be something wrong with my RAID controller or something. Anyways, I still got stuck with this ....

---

