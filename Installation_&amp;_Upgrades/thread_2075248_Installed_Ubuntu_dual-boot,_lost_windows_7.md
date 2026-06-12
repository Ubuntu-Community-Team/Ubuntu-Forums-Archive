---
title: "Installed Ubuntu dual-boot, lost windows 7"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Jam0 on 2012-10-23
I have a 2 hhd system ("C" and "E") and tried to install Ubuntu in the 2nd drive "E". It installed but apparently not in the partition because I can see and access all my files on that drive while in Ubuntu. I am pleased about that because I am in the process of recovering them to an external hard-drive.

Unfortunately windows 7 on disk "C" can not be accessed, booted or found on my windows recovery disk. I ran Ubuntu boot repair and got this report [http://paste.ubuntu.com/1297931/](http://paste.ubuntu.com/1297931/)  

I sent that to the email address and Yann was kind enough to analyse it and reply "your windows was installed on RAID, which is now broken" 

I am almost positive that my Windows was not installed in RAID -- I had 2 separate drive-letters and the drives were not mirrored.

Ubuntu was also not installed in RAID because it did not wipe-out my data on all disks as I read it does when you choose that option.

As I said I am in the process of copying all the data (created in windows) I can see while in Ubuntu, which is the entirety of what was on my E drive. 

After that, obviously I would love to restore my C drive if there is any possibility of that.

Any assistance welcomed and greatly appreciated

---

### Post by darkod on 2012-10-23
Unfortunately having C and E in windows doesn't mean two disks. It only means two partitions which can be on one disk, or two separate disks.

Microsoft really messed it up when they started calling them "drive C" because drive is the synonim for a physical disk (Hard Disk Drive) and in windows C is usually a partition and doesn't mean it's a disk. They should have just called it "partition C", as it is.

Let me see if I can take a look at your bootinfo too.

---

### Post by darkod on 2012-10-23
You might be lucky. :) It seems the 1TB disk was used in raid earlier and has meta data remains. Windows ignores these so while you were running only windows everything looked normal.

But ubuntu doesn't ignore the meta data and is confused whether there is raid array or not.

You are probably right that there was no raid, especially since sda is 500GB and you rarely make raid from 500GB and 1TB disks. Plus you seem confident you didn't have one.

The way it looks to me, you should be OK by simply removing the meta data which you can do from ubuntu or from the ubuntu cd running in live mode:
sudo dmraid -Er /dev/sdb

That would remove the meta data from sdb and that's it. It should leave all the data intact and windows working, but if you can make a backup before running the command, it's better to do it.

---

### Post by MickKi on 2012-10-23
> **Jam0 said:**
> I have a 2 hhd system ("C" and "E") and tried to install Ubuntu in the 2nd drive "E". It installed but apparently not in the partition because I can see and access all my files on that drive while in Ubuntu.

Your Ubuntu was installed in the first hard drive /dev/sda.

Your WIndows is still it seems on the second drive /dev/sdb.  The second drive is 1TB.

You can edit grub to point it to your WIndows boot partition (/dev/sdb1).  I'm not at a Ubuntu machine right now to guide you on the specifics.  Look in /etc/default/grub and /etc/grub.d/ to find a file which contains a MSWindows boot menu entry and change it like this:

menuentry "Windows 7 (loader)  (on /dev/sdb1) {
           set root=(hd1,0)
           chainloader +1
}

Then run sudo update-grub and reboot.  If the MSWindows OS was installed in a single partition, then the above should be able to boot it - if however it was installed in a MSWindows pseudo-RAID, then it may well be irrecoverable ...

HTH.

---

### Post by Jam0 on 2012-10-23
> **darkod said:**
> You might be lucky. :) It seems the 1TB disk was used in raid earlier and has meta data remains. Windows ignores these so while you were running only windows everything looked normal.

But ubuntu doesn't ignore the meta data and is confused whether there is raid array or not.

You are probably right that there was no raid, especially since sda is 500GB and you rarely make raid from 500GB and 1TB disks. Plus you seem confident you didn't have one.

The way it looks to me, you should be OK by simply removing the meta data which you can do from ubuntu or from the ubuntu cd running in live mode:
sudo dmraid -Er /dev/sdb


That would remove the meta data from sdb and that's it. It should leave all the data intact and windows working, but if you can make a backup before running the command, it's better to do it.

Thanks so much Darkod -- my spirits are lifted!

So I open a terminal and type in "sudo dmraid -Er /dev/sbd" and hit enter?
I am in the process of backing up the "E" drive so will try it after that. Is there a preference to do it "live" from the CD or from Ubuntu?

I have a sneaking suspicion that the 1TB disk that the guy sold me as new was not new. Anyway, if this ends well then all is well.

Thanks again,
Jam0

---

### Post by darkod on 2012-10-23
Yes, you only execute it in terminal. No preference between live cd and hdd installation.

It will ask you to confirm you want the meta data removed, confirm and that should be it. Win7 is not detected because ubuntu thinks the disk is part of raid and "doesn't look inside it correctly". As consequence, it can't see the win7 boot files.

I think all will be fine after removing the meta data, you will only need to run:
sudo update-grub

to scan the disks again and create the win7 entry.

PS. From what I can tell, there is no way for a brand new disk to come with this meta data on it.

---

### Post by Jam0 on 2012-10-23
> **MickKi said:**
> Your Ubuntu was installed in the first hard drive /dev/sda.

Your WIndows is still it seems on the second drive /dev/sdb.  The second drive is 1TB.

You can edit grub to point it to your WIndows boot partition (/dev/sdb1).  I'm not at a Ubuntu machine right now to guide you on the specifics.  Look in /etc/default/grub and /etc/grub.d/ to find a file which contains a MSWindows boot menu entry and change it like this:

menuentry "Windows 7 (loader)  (on /dev/sdb1) {
           set root=(hd1,0)
           chainloader +1
}

Then run sudo update-grub and reboot.  If the MSWindows OS was installed in a single partition, then the above should be able to boot it - if however it was installed in a MSWindows pseudo-RAID, then it may well be irrecoverable ...

HTH.
Thanks Mickki, however windows is installed on the 500g drive (C) and Ubuntu appears to be installed on the 1tb drive (E) as that is the drive I have available to me when in Ubuntu.

---

### Post by Jam0 on 2012-10-23
> **darkod said:**
> Yes, you only execute it in terminal. No preference between live cd and hdd installation.

It will ask you to confirm you want the meta data removed, confirm and that should be it. Win7 is not detected because ubuntu thinks the disk is part of raid and "doesn't look inside it correctly". As consequence, it can't see the win7 boot files.

I think all will be fine after removing the meta data, you will only need to run:
sudo update-grub

to scan the disks again and create the win7 entry.

PS. From what I can tell, there is no way for a brand new disk to come with this meta data on it.
Thanks Darkrod -- I can't wait to try it, but it is going to be a few hours as the back-up is going to take a while. 

I will certainly keep you abreast of the situation as it happens :)

Much appreciated

BTW I am also located in Spain. San Pedro de Alcantara.

---

### Post by MickKi on 2012-10-23
> **Jam0 said:**
> Thanks Mickki, however windows is installed on the 500g drive (C) and Ubuntu appears to be installed on the 1tb drive (E) as that is the drive I have available to me when in Ubuntu.

Hmm ... not according to your pastebin file.  Ubuntu is installed in /dev/sda2 on an ext4 fs and MSWindows on /dev/sdb1 on an NTFS fs.  Yes?

---

### Post by Jam0 on 2012-10-24
Unfortunately it didn't seem to work. I applied the command and the updated the grub, and I only have Ubuntu, advanced options for Ubuntu and memory tests on the menu.

I ran another boot-repair which generated this url: [http://paste.ubuntu.com/1302320/](http://paste.ubuntu.com/1302320/)

I do have a windows recovery-disk that did not "automatically" fix the problem before; I haven't tried it since I deleted the raid meta data.  This article describes using it to fix boot problems  malwaretips.com/blogs/fix-computer-wont-start/   

Any opinions/help much appreciated

Jam0

---

### Post by MickKi on 2012-10-24
sudo mkdir /mnt/Windows7

sudo mount -t ntfs-3g /dev/sdb1 /mnt/Windows7

If successful, ls -la /mnt/Windows7 to see the contents of your MSWindows boot partition.  Then you can try the same with /dev/sdb2 (assuming that it is accessible).

Alternatively, use something like testdisk to recover the partition table and potentially any files on it.

HTH.

---

### Post by Jam0 on 2012-10-24
> **MickKi said:**
> sudo mkdir /mnt/Windows7

sudo mount -t ntfs-3g /dev/sdb1 /mnt/Windows7

If successful, ls -la /mnt/Windows7 to see the contents of your MSWindows boot partition.  Then you can try the same with /dev/sdb2 (assuming that it is accessible).

Alternatively, use something like testdisk to recover the partition table and potentially any files on it.

HTH.

Thanks Mickki, so those are separate commands to be tried separately? (I just want to be clear because this stuff is new to me). 

After I enter a command do I need to update the grub?

Thanks,
Jam0

---

### Post by Jam0 on 2012-10-24
I tried the first command you listed and  I got:   mkdir: cannot create directory ' /mnt/Windows7' : File exists

---

### Post by darkod on 2012-10-24
Hold on, is ubuntu booting right now or not?

If it is, no need for the command line. You can open the file browser (Nautilus) and open your 1TB disk (partition) in it. That should allow you to browse the files.

Take a look what you have on the 1TB partition since according to the script it doesn't look like a windows installation. Is it possible that it was on the 500Gb disk and you overwrote it with ubuntu?

It's not just a question of missing boot files, there is no win7 reported on /dev/sdb1 at all.

---

### Post by Jam0 on 2012-10-24
> **darkod said:**
> Hold on, is ubuntu booting right now or not?

If it is, no need for the command line. You can open the file browser (Nautilus) and open your 1TB disk (partition) in it. That should allow you to browse the files.

Take a look what you have on the 1TB partition since according to the script it doesn't look like a windows installation. Is it possible that it was on the 500Gb disk and you overwrote it with ubuntu?

It's not just a question of missing boot files, there is no win7 reported on /dev/sdb1 at all.

Darkod the windows installation is on the 500gb disk

---

### Post by Jam0 on 2012-10-24
Does that mean windows was overwritten with ubuntu?

When I did the installation I was careful to choose "free space"

---

### Post by darkod on 2012-10-24
> **Jam0 said:**
> Does that mean windows was overwritten with ubuntu?

Probably yes. Only linux partitions are reported on the 500GB disk, called /dev/sda.

```
Disk [COLOR="Red"]/dev/sda: 500.1 GB[/COLOR], 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046     1,953,791     1,951,746   5 Extended
/dev/sda5               2,048     1,953,791     1,951,744  82 Linux swap / Solaris
/dev/sda2    *      1,953,792   148,649,983   146,696,192  83 Linux
```

No ntfs partitions.

You might be able to save something, but the chances are low. If you want to try, stop booting ubuntu from the hdd right away and use only the cd in live mode. The longer ubuntu runs from the hdd, the less chance to save previous partitions.

---

### Post by black veils on 2012-10-24
the 500gb only has linux stuff on it, so that would seem to be the case, yes.

the 1tb has a Windows filesystem on it, but that could just be data (not operating system).

---

### Post by Jam0 on 2012-10-24
> **darkod said:**
> Probably yes. Only linux partitions are reported on the 500GB disk, called /dev/sda.

```
Disk [COLOR=Red]/dev/sda: 500.1 GB[/COLOR], 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046     1,953,791     1,951,746   5 Extended
/dev/sda5               2,048     1,953,791     1,951,744  82 Linux swap / Solaris
/dev/sda2    *      1,953,792   148,649,983   146,696,192  83 Linux
```No ntfs partitions.

You might be able to save something, but the chances are low. If you want to try, stop booting ubuntu from the hdd right away and use only the cd in live mode. The longer ubuntu runs from the hdd, the less chance to save previous partitions.
I had Ubuntu on for hours during the back-up of the 1tb disk, and have also rebooted it many times.

So what you're saying is that windows is pretty much gone and the best I could do is perhaps recover some files.

Thanks for your help. I guess I will buy an OEM copy of windows and reinstall. I would like to have Ubuntu too and have it set-up correctly from the start. 

Might I run into any problems with a fresh install?

---

### Post by Jam0 on 2012-10-24
> **black veils said:**
> the 500gb only has linux stuff on it, so that would seem to be the case, yes.

the 1tb has a Windows filesystem on it, but that could just be data (not operating system).
Yeah, the windows was installed on the 500gb disk before I acquired the 1tb disk. Like I said I was sure to specify "free space" when installing Ubuntu, but I guess it didn't listen. I was trying to install it on the 1tb disk to ensure that it was separate from windows. I don't know if that raid meta data had something to do with all of this.

---

### Post by Jam0 on 2012-10-24
What I think happenned is it thought I was using raid when I was installing, then it just overwrote everything. I didn't realize the potential danger or I would have been a million  times more careful. My bad. I was actually following a youtube video that made it look like the simplest process in the world. Thanks for everybody's help and responses,

Jam0

---

### Post by black veils on 2012-10-24
it can be easy, it just depends.

but no matter what, always backup before making any changes to the hdd/partition/system, just in case, as you never know what might happen, and people make mistakes, so why risk losing the data/system.

---

### Post by Jam0 on 2012-10-24
Thanks.

The one program I really want back from that 500gb drive is photoshop. Any suggestions on how I might recover that one program?

I was able to see and recover everything from the 1tb disk while in ubuntu. I wonder why I can't see anything on the 500gb disk. Ubuntu only uses a couple of gb for its' installation files, right? I would think if it wiped the disk clean, installation would have taken much longer than it did.

---

### Post by black veils on 2012-10-24
it wiped the 500gb clean, and installed ubuntu.

---

### Post by darkod on 2012-10-24
When you delete files or a partition in this case, it doesn't literary get deleted. Only the partition table is modified to tell the computer the old partition doesn't exist any more.

The ubuntu size is far less than 500GB and if you use testdisk to try and recover the old partitions, you might be able to recover most of the data. Only the data that was physically overwritten by the ubuntu files will be lost.

But this process would mean you lose your ubuntu also, because it will try to recover the old partitions in place of the current ubuntu partitions. You will have to do it from live mode, and as I said, if you want to try, stop booting from the hdd right away so that there are no more files and changes written.

You can download and run testdisk from live mode. Here are the step by step instructions. If you need advice, it's best to do the Deeper Search and post the screenshot. After that we can see what you can recover or not.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by MickKi on 2012-10-24
> **Jam0 said:**
> Thanks Mickki, however windows is installed on the 500g drive (C) and Ubuntu appears to be installed on the 1tb drive (E) as that is the drive I have available to me when in Ubuntu.

I think you need to stop for a minute and go back to the information you have been pasting in pastebin.

This is what the 500G Seagate disk contains:
```
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1048kB  1000MB  999MB   extended
5      1049kB  1000MB  999MB   logical   linux-swap(v1)
2      1000MB  76.1GB  75.1GB  primary   ext4            boot
```

There is an ext4 fs in the second partition which contains your Ubuntu installation.  It is 75.1G.  Your swap partition is a logical partition 999MB.  I assume that the rest of the disk is empty.

Now look at what you pasted about the 1T Western Digital disk:
```
Model: ATA WDC WD10EUCX-73Y (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  921GB  921GB  primary  ntfs         boot
```
It contains only 1 partition, 921GB with NTFS fs on it.  It is not optimally partitioned for 4096 byte sectors that terrabyte disks have, but that's not important right now.  Ubuntu has created a mount point for it, under /mnt/boot-sav/sdb1 - it thinks it is in a RAID configuration.

The repair you attempted showed you an error - only half of the RAID configuration appears to be available:
```
ERROR: sil: wrong # of devices in RAID set "sil_biaeaebifgag" [1/2] on /dev/sdb
```

This indicates that the 1T Western Digital disk had a brother which has now gone missing and contains the other half of the MSWindows installation.  If this was a RAID mirror, then you should be able to recover the content using testdisk/photorec, or similar software.

Now, if you have been pasting the wrong things in pastebin, then it might be that your Ubuntu was installed in the 1T disk - but that's not what pastebin is showing ...  yes?

---

### Post by Jam0 on 2012-10-24
Thanks guys for the responses.

Mickki, yeah, Ubuntu was inadvertently install on the 500gb disk.

Darkod, I think I'm going to try testdisk. I have to travel and will be back in a week, and will try it then. I can always reinstall Ubuntu,

If I fresh install Windows on one disk, unplug it and then fresh install Ubuntu on the other one, is that a good way to do it? I would still want some space on the Ubuntu disk to store some windows data. In other words, for windows to have access to part of that disk.

---

### Post by darkod on 2012-10-24
You can use as much of the 500GB as you want for ubuntu. Install it at the beginning of the disk, giving the partitions the size you want. Then after ubuntu is working, create one or more ntfs partitions on the rest of the disk. Windows will be able to use them without any problem.

---

