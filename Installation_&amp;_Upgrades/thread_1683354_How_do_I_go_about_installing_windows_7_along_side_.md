---
title: "How do I go about installing windows 7 along side my current ubuntu instillation?"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by JLangford on 2011-02-07
Hey there.

I recently put ubuntu on my laptop in hope that most of my games would run through wine, some did and some didn't. 

Anyway, long story short, I have ubuntu on my laptop and I want to re install windows onto a separate partition, keeping my ubuntu instillation in tact and set as my deafault OS.

I'm very new to ubuntu and the only guides i've seen are fairly complex.
I was just wondering if anyone could point me in the right direction?

Thanks in advance.

p.s. Is there maybe a way to create an image of my current ubuntu instillation/settings/apps etc. just in case I do something wrong and lose everything?

---

### Post by Rubi1200 on 2011-02-07
Well, you should definitely make backups before proceeding!

Clonezilla is a good option:
[http://clonezilla.org/](http://clonezilla.org/)

To help us advise you better, please run the following command in the terminal on Ubuntu:

```
sudo parted -l
```

(lowercase L not 1).

Post the output here.

---

### Post by JLangford on 2011-02-07
I'll take a look at clonezilla now, thanks.


I ran the command and here is the output

```
Model: ATA Hitachi HTS72503 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  311GB  311GB   primary   ext4            boot
 2      311GB   320GB  8871MB  extended
 5      311GB   320GB  8871MB  logical   linux-swap(v1)


Model: Generic- Multi-Card (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  3732MB  3731MB  primary   fat32
 2      3733MB  3965MB  232MB   extended
 5      3733MB  3965MB  232MB   logical   linux-swap(v1)



```

Once again, thanks.

---

### Post by JLangford on 2011-02-07
Bump. :p

---

### Post by Elfy on 2011-02-07
Please do not bump so soon, no more than once in 24 hours.

---

### Post by JLangford on 2011-02-07
Ahh, okay, sorry about that, I'm just so desperate to get my laptop sorted haha.

But I guess other people need help just as much as I do.

---

### Post by oldfred on 2011-02-07
You need to shrink your / (root) partition.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Windows has to have a primary NTFS partition to install into. You can create a sda3 in the free space you create and install there. If you want to share data between windows & Linux you may want to also create another NTFS partition for shared data. That can be either primary or logical inside the extended. If you make it logical you will have to expand the extended left to make space inside the extended for a logical partition.

Windows will put its bootloader into the MBR. You have to reinstall grub2 from a liveCD, so be sure to have a working liveCD.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by presence1960 on 2011-02-07
> **JLangford said:**
> I'll take a look at clonezilla now, thanks.


I ran the command and here is the output

```
Model: ATA Hitachi HTS72503 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  311GB  311GB   primary   ext4            boot
 2      311GB   320GB  8871MB  extended
 5      311GB   320GB  8871MB  logical   linux-swap(v1)


Model: Generic- Multi-Card (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  3732MB  3731MB  primary   fat32
 2      3733MB  3965MB  232MB   extended
 5      3733MB  3965MB  232MB   logical   linux-swap(v1)



```

Once again, thanks.

You want to shrink sda1 to create space for windows 7. Boot the Ubuntu Live CD/USB. Choose "try ubuntu". When the desktop loads go System > Administration > Gparted Partition Editor. You can then safely resize sda1 to make space for Windows. You can either leave it as unallocated space or create a primary NTFS partition. When completed reboot and boot the windows install DVD. Install windows to the unallocated space or the NTFS partition- whichever one you chose. When the installation is completed reboot and make sure windows boots.

Next you must reset the MBR to use GRUB 2. Boot the ubuntu Live CD/USB. Choose "try ubuntu." When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```This will mount your ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```This will reset the MBR to have GRUB 2 and point it to sda1. You can then reboot and you should be good to go.

P.S. I guess oldfred types faster than I do

If you have a recovery partition or a recovery CD/DVD you may not be able to do the above. Most, but not all vendors, have the recovery process run a script which formats the entire disk. Anything on there will be lost. I know Toshiba, among a few others, allow you to install to a separate NTFS partition without erasing the entire disk. be sure you know what the exact case is in your situation by consulting your documentation that came with the lappie.

If you have a retail windows DVD you are safe.

---

### Post by JLangford on 2011-02-07
Wow, thank you both so much!

I have recovery disks that format the whole HDD but I have access to a variation of every windows OS because I'm a student, so that's not a problem.

Again, thank you both, these guides are way more straight forward than the ones I found online.

---

### Post by presence1960 on 2011-02-07
> **JLangford said:**
> Wow, thank you both so much!

I have recovery disks that format the whole HDD but I have access to a variation of every windows OS because I'm a student, so that's not a problem.

Again, thank you both, these guides are way more straight forward than the ones I found online.

you are welcome.

---

### Post by Rubi1200 on 2011-02-07
My thanks too to oldfred and presence1960 for this great advice.

Hope you get things set up the way you want.

Good luck!

---

### Post by JLangford on 2011-02-07
Hmm, I seem to be having a problem.

I installed windows on a seperate partition, and as expected it overwrite the boot loader, but as I restored GRUB it now takes me straight into ubuntu, the grub menu doesn't show up at all.

Could it be that its configured not to show up? Are there settings to configure GRUB somewhere?

Thanks :)

---

### Post by oldfred on 2011-02-07
Grub does not know you installed windows. You have to ask it to look and see if you changed something. Silly computers only do what you tell them to do, not what you want them to do.

```
sudo update-grub
```

---

### Post by JLangford on 2011-02-07
YAY! It works now, thanks man!

Props to everyone in this thread for helping me out!

Thanks.

---

### Post by oldfred on 2011-02-07
You are welcome. Happy Ubuntu-ing.

---

### Post by presence1960 on 2011-02-07
> **oldfred said:**
> You are welcome. Happy Ubuntu-ing.

+1

Enjoy ubuntu.

---

