---
title: "installer cannot create a shared fat32 partition with win 7"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Papex on 2010-10-12
Why would that be?

I have win 7 installed on a primary partition along with two other primary partitions containing a recovery partition and system files partitions. (don't know exactly what the latter is for.) 

I made a defrag and resized the win partition to make some free space for a primary ubuntu partition.
I then inserted the 10.10 live disc and created a fat32 shared partition, a root (/), a /home Nd a swap in the advanced gparted menu, BUT every time I try to initiate the installation I get an error message saying that installer couldn't create the fat32.

What am I doing wrong here?

Thanks in advance.

---

### Post by mikechant on 2010-10-12
OK, you've pre-created your partitions in gparted; what exactly are you doing in the installer when it gets to the partitioning stage? Or does the installer not get that far?

---

### Post by dondos on 2010-10-13
Same problem here.

During the installation of 10.10 I chose the manual partitioning. I wanted my second hard-disk like this: /dev/sdb1 as root (ext4), /dev/sdb2 as swap, /dev/sdb3 as shared (fat32). But the installation could not continue.

I beleive there is a bug in gparted. I will try to repeat the procedure and submit a clear bug-report. I think that the problem has to do with the FAT32(vfat) partition I try to create.

The only solution was to reboot with my previous LiveCD (ubuntu 9.04) and partition the hard-disk with this version. Then I continued installing 10.10. Now everything seems fine.

---

### Post by Papex on 2010-10-13
Well, there might be a bug in Gparted on the live CD, in my case however it turned out that I hadn't noticed that there was already four primary partitions on the HD (An OEM windows recovery partition among others).

But Gparted didn't inform me on this on the Live CD. It actually accepted my setup and then came up with the error message in the running pre-installation proces (one of the new things in 10.10) saying that Gparted was unable to create a FAT 32 partition, but it actually allowed me to continue the installation proces if I wanted to. 

I ended up installing Ubuntu without the FAT 32 partition leaving it as blank space on the HD.
After Installation I downloaded Gparted and NOW I was told that the reason for not being able to make the partition was that I alreaddy had four primary partition.
I then deleted a recovery partition and then created the FAT 32 partition.


All in all: my mistake and (perhaps) Gparted on the live image ;-)

---

### Post by efflandt on 2010-10-13
On a drive with the usual msdos partition table, you can only have 4 primary or extended partitions on a drive.  So if there are already 3 partitions on a drive, the correct way to add more than one additional partition would be to create an "extended" partition for the rest of the drive.  Then you can make any number of "logical" partitions within the extended partition.

---

