---
title: "Dual boot with Win7 not working? (Installation)"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by LawlCakes on 2012-04-17
Okay, My first issue was nomodeset..After that was fixed I can't seem to install Ubuntu 10.10 I made a new partition on /dev/sda called sda2 Reformatted it everything was working, Then I go to INSTALL it and it gives ONLY /dev/sda for the boot loader. Then shows nothing in the box there. Also it never gives me the option for advanced setup...Then I push install now and it says "No root file system defined" I have tried everything I know of to fix this..Any ideas? Please help...I really can't afford another Hard drive just for Linux. (By the way Win7 is installed on /dev/sda1)I have even re-burned it 2 times. Still same issue.

Specs:
Intel Q6600 
ST31000340AS Barracuda 7200.11 SATA 3Gb/s 1-TB
e-Geforce 9800 GX2

---

### Post by Bucky Ball on 2012-04-17
When you get to the partitioning section of the install choose 'Something Else' to manually partition. 

No need to create a partition for Ubuntu using Windows (and no point) as Ubuntu can't install on it anyhow. Needs to create its own EXT* partition for that. Just install Windows (on say 30Gb partition) and leave the rest free space.

Then when you get to 'Something Else' you should see the Win partition(s) on NTFS and the rest free space.

A point to remember: four primary partitions on one physical hard drive is the max. To get around this create an extended partition and logical drives inside that. Ubuntu will happily live inside an extended partition on a logical drive, Windows will not. Best on first drive, first partition. ;)

I have included a screenshot of my partition setup to make things a little clearer. All NTFS partitions are owned by Windows 7 apart from sda10 = Misc which is a shared partition between both OSs. As you can work out, my three Ubuntu installs are inside the extended partition on logical drives and all use the same /home partition. Windows has the three primary drives. ;)

---

### Post by LawlCakes on 2012-04-17
> **Bucky Ball said:**
> When you get to the partitioning section of the install choose 'Something Else' to manually partition. 

No need to create a partition for Ubuntu using Windows (and no point) as Ubuntu can't install on it anyhow. Needs to create its own EXT* partition for that. Just install Windows (on say 30Gb partition) and leave the rest free space.

Then when you get to 'Something Else' you should see the Win partition(s) on NTFS and the rest free space.

A point to remember: four primary partitions on one physical hard drive is the max. To get around this create an extended partition and logical drives inside that. Ubuntu will happily live inside an extended partition on a logical drive, Windows will not. Best on first drive, first partition. ;)

I have included a screenshot of my partition setup to make things a little clearer. All NTFS partitions are owned by Windows 7 apart from sda10 = Misc which is a shared partition between both OSs. As you can work out, my three Ubuntu installs are inside the extended partition on logical drives and all use the same /home partition. Windows has the three primary drives. ;)



Thanks for the reply, I have also tried leaving the free space there. Still won't work. Plus I'm installing Ubuntu 10.10 not 11.04+ So I don't have the "Something Else" option. What it does on mine is just skip any advanced partition settings etc and goes straight to where you install the boot loader. And will only give /dev/sda as the option and nothing else. And it won't even work with that option. I'll try it on a extended / logical, and i'll be back with my results.

---

### Post by oldfred on 2012-04-17
You want to install the grub2 boot loader to sda or the MBR - master boot record of the drive. BIOS based Computers only boot from MBR, so if you leave Window's boot loader in the MBR you will only be able to boot Windows. Grub2's boot loader will let you boot both Windows & Ubuntu.

They renamed manual install to Something Else in the new verions. With manual install you create if you have not already created them, partiitons and specify which is / (root), /home (if desired) and swap.

Some examples of installs and issues with 10.10:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by LawlCakes on 2012-04-24
No luck with that..I got screens. Still won't work and still does the same thing...Ideas? But when I plug in my external 500GB hard drive. It will give me the option for  "Advanced" (Last screen) Yet it still won't show my main drive. wtf? :mad:

---

### Post by darkod on 2012-04-24
If there is any error or corruption in the partition table, it will not list the partitions during the install.

Boot into live mode, open terminal and post the output of these two commands:
sudo fdisk -l (small L)
sudo parted /dev/sda print

---

### Post by techsupport on 2012-04-24
> **LawlCakes said:**
> No luck with that..I got screens. Still won't work and still does the same thing...Ideas? But when I plug in my external 500GB hard drive. It will give me the option for  "Advanced" (Last screen) Yet it still won't show my main drive. wtf? :mad:

Shrink your Partition in Windows. Allow some space to install Ubuntu first. (?)

Ubuntu used to have an option to shrink the hard drive and create a Side-by-side install in Ubuntu 10.10 Ubiquity installer. I don't know why they removed it in 12.04.  Ugh. You need to boot back into Windows. Shrink your partition to create some space first and then install as normally.

---

### Post by LawlCakes on 2012-04-24
> **darkod said:**
> If there is any error or corruption in the partition table, it will not list the partitions during the install.

Boot into live mode, open terminal and post the output of these two commands:
sudo fdisk -l (small L)
sudo parted /dev/sda print


```


sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd86af86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      101489   815209192+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          101489      121602   161552384    5  Extended
/dev/sda5          101490      121602   161551360   83  Linux

``````
 
sudo parted /dev/sda print

Model: ATA ST31000340AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type      File system  Flags
 1      32.3kB  835GB   835GB  primary   ntfs         boot
 2      835GB   1000GB  165GB  extended
 5      835GB   1000GB  165GB  logical   ext4

```

---

### Post by LawlCakes on 2012-04-24
> **techsupport said:**
> Shrink your Partition in Windows. Allow some space to install Ubuntu first. (?)

Ubuntu used to have an option to shrink the hard drive and create a Side-by-side install in Ubuntu 10.10 Ubiquity installer. I don't know why they removed it in 12.04.  Ugh. You need to boot back into Windows. Shrink your partition to create some space first and then install as normally.


I did..I gave Ubuntu 150GB. Ext4

---

### Post by oldfred on 2012-04-24
Are you installing to sda or sdb, you show screen shots of both with a Linux partition on sda.

With 2 drives you do need to use manual install or Something else but then you have to create partitions and tell the system what they are used for, typically / (root), /home & swap although even /home is optional. You also then need to use the combo box at the bottom to choose which drive's MBR you want to install the grub2 boot loader into. Usually the same drive as you install system into, but it defaults to sda unless told otherwise.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

You can use gparted to partition in advance:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2012-04-24
I am not 100% sure, but try this. I suspect the disk has raid meta data left overs if it was used in raid before. This can make it not show the partitions to prevent you from installing over your raid array. Boot into live mode and in terminal try:
sudo dmraid -E -r /dev/sda

If that asks you if you want to remove raid meta data, confirm. Try again to install.

---

### Post by LawlCakes on 2012-04-24
> **oldfred said:**
> Are you installing to sda or sdb, you show screen shots of both with a Linux partition on sda.

With 2 drives you do need to use manual install or Something else but then you have to create partitions and tell the system what they are used for, typically / (root), /home & swap although even /home is optional. You also then need to use the combo box at the bottom to choose which drive's MBR you want to install the grub2 boot loader into. Usually the same drive as you install system into, but it defaults to sda unless told otherwise.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

You can use gparted to partition in advance:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


sdb is my 500GB External. I don't want to install it on there. Was just showing how "IT" shows up but my main drive will not...I want to install it on sda not sdb.

---

### Post by LawlCakes on 2012-04-24
> **darkod said:**
> I am not 100% sure, but try this. I suspect the disk has raid meta data left overs if it was used in raid before. This can make it not show the partitions to prevent you from installing over your raid array. Boot into live mode and in terminal try:
sudo dmraid -E -r /dev/sda

If that asks you if you want to remove raid meta data, confirm. Try again to install.


Works!!!!! Thanks!!!!!

---

### Post by LawlCakes on 2012-04-24
One last question..For the boot loader. Do I install it to /dev/sda or /dev/sda1 (Windows Loader) or /dev/sda2

I don't want to **** up my NTFS partition...

---

### Post by darkod on 2012-04-24
> **LawlCakes said:**
> One last question..For the boot loader. Do I install it to /dev/sda or /dev/sda1 (Windows Loader) or /dev/sda2

I don't want to **** up my NTFS partition...

/dev/sda, always without a number.

The number means a partition and the bootloader almost always goes to the MBR of the disk. The MBR is just the device name, without any number.

---

