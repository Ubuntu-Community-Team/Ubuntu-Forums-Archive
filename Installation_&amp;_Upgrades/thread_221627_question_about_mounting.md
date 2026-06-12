---
title: "question about mounting"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by linuxnoob40 on 2006-07-23
not sure if this is the correct place for this question butn here goes...i have a 30 gig drive that has all the files i wanted to save from my windows drive i made it fat 32 and have folowed the guide at ubuntuguide it says to do this
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

i have done this and got this msg for my trouble
mount: special device /dev/hda1 does not exist

outside of pulling out my hair ](*,)  i have no idea what to do next so im asking the linux gods to help.
btw i can see the drive as new volume but thats it when i try to open it i get a error msg saying: unable to mount the selected volume error: device /dev/hdb1 is not removable

error: could not execute pmount

any help would be much apreciated

---

### Post by ahallubuntu on 2006-07-23
Er, what do you mean exactly that you "made" it FAT32?  It was originally FAT32 before you copied the files onto it, right?  (You didn't try to "convert" it to FAT32 from NTFS?)

Are you sure you have the right partition number?  Try this:

sudo fdisk /dev/hda -l

to show your partitions.  Does your partition also list with the right partition type?  (FAT32?)

---

### Post by ciscosurfer on 2006-07-23
First, you need to make sure that you are mounting the right drive.  In the HowTo @ Ubuntu Guide, they use hda1 b/c that's typically your mount point...mine is sda1 because I use an SATA disk (and so it's on the first SATA drive, first partition).  Please type this into a terminal and make sure you are trying to mount the correct disk/partition (copy and paste this code)```
sudo fdisk -l
```Then substitute in the correct disk/partition into the code you previously provided.

---

### Post by linuxnoob40 on 2006-07-23
Thank you =)

---

