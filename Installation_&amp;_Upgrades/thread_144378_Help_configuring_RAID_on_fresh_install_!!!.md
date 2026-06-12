---
title: "Help configuring RAID on fresh install !!!"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by Joe Driller on 2006-03-14
I have a Supermicro P6DBE MoBo with 2x PIII500 Cpu´s, 256 Mb RAM, 2x15 Gb IDE HD, 2x4,6 Gb SCSI2 HD with Advansys 3940UW controller, a 50X IDE CD-ROM and a 4,3 Gb SCSI HD and SCSI CD-RW hanging from Adaptec AHA-2940.

I am trying to install Kubuntu 5.10 as follows:

RAID0 with SCSI2 to install system.
4,3 SCSI HD for swap and a partition with fat32 to share with "Bill Gates friends" via Network
RAID1 with 15 Gb IDE's for /home.


I configure a whole 4.6 Gb partition on both  SCSI2 HD as "physical volume for raid"
then go to "configure software RAID" and make a RAID0 MD.

At this point I go to guided partitioning and chose "Erase entire disk and use LVM: RAID0 device #0 - 9,1 Gb Software"


Every time I try it system say:



Error informing the kernel about modofications to partition /dev/md/0p1 - Invalid argument. This means Linux won't know about any changes you made to dev/md/0p1 until you reboot - so you shouldn't mount it or use it in any way before rebooting.


If I choose ignore system says the same for /dev/md/0p5

If I choose ignore too systems returns to partitioning menu where I can see RAIDo device #0 partitioned as follows:

#1 primary 255.0 Mb ext3 /boot
#5 logical   8.9 Gb  lvm



Any suggestions ????


Thanks in advance.

Jose Coma

---

### Post by berrida on 2006-09-10
Hi Jose,

have you read the [File Server on LVM on RAID]("https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28lvm%29#head-f53cec4bda1abc8f8662e9fc8a31242198bf5a42") document?

I was having similar issue but as the author suggests, if after you've set-up and configured the RAID you ALT-F2 to the terminal and run cat /proc/mdstat/ you'll see the build status of the RAID.  I waited until the RAID was fully synchronised before I set up the LVM.

This doesn't prevent the /dev/md/0p1 error but if you chose Ignore and set-up the LVM you should be golden (at least it worked for me).

Good luck.

Adrian

---

