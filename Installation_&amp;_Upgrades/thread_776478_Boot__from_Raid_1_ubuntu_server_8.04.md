---
title: "Boot  from Raid 1 ubuntu server 8.04"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by rgotten on 2008-04-30
I am in the process of installing my server and have being trying for the last few weeks differet options on installing my raid and be able to boot. I am installing the boot on Raid 1 128mb, Swap on Raid 1 (2gb), the root on raid 5 (10 gb) and the rest for home on Raid 5 ( aprox. 960 gb).
For doing this i am using 3 hard drive 500 ngb each. Before the 8.04 relaese i had to install the boot instruction on each one of the hard drive (device (hd1) /dev/sda
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdb
root (hd1,0)
setup (hd1)
device (hd1) /dev/sdc
root (hd1,0)
setup (hd1)
so if one fails the raid can be started from the other hard drive. With version 8.04, when i disconect either of the hard drive it appears to boot and i get a message that says: start the raid in degrade (or somethng similar), with the command mdadm -R /dev/mdx ( in version 7.10, i have to install the boot instruction in each one of the hard drive, see: [https://launchpad.net/ubuntu/+bug/58894](https://launchpad.net/ubuntu/+bug/58894)). Since i am getting this message, does this mean that the newer version has the bug fixed in regards to the instruction on how to boot in each one of the hard drive??

How can i check each hard drive to be sure they have this instruction and that i have installed grub also on the second disk's (/dev/sdb) master boot record (MBR), as well as the third. ??

rgotten

---

### Post by luptonma on 2008-05-02
rgotten:

I just set up Ubuntu Server 8.04 with a RAID 1 /boot partition similar to what you describe.  I had a bit of trouble because the drive letters assigned by the Ubuntu live DVD were different than the ones assigned when the 8.04 server booted so I had to match the drive IDs to keep things straight.  

I believe you asked how to check that all the drives in the /boot array have GRUB in the MBR and I think you asked how to make sure all the stage 2 files are on each disk?

Both checks can be done from the command line:  

Presumably when you boot your RAID array automaticlly assembles itself.  To check the files on each of the mirrors just stop the array and remount the individual mirror partitions under /mnt.  I have /dev/sde1 and /dev/sdf1 mirrored as /dev/md0 so for me the commands are:
```
sudo mdadm --stop /dev/md0
sudo mkdir /mnt/boot1
sudo mkdir /mnt/boot2
sudo mount -t ext3 /dev/sde1 /mnt/boot1
sudo mount -t ext3 /dev/sdf1 /mnt/boot2
```

Note that the mount command demands that you specify the file type as it can't automatically determine it for a partition that's been part of a RAID array.  Obviously this only makes sense for RAID 1 arrays.  I would not recommend trying to remount part of a RAID 5 or RAID 0 array this way.  

Then you can use diff to compare the two directories recursively:
```
diff -r /mnt/boot1 /mnt/boot2
```

When you are done you can unmount boot1 and boot2 and assemble the array
```
sudo umount /mnt/boot[12]
sudo mdadm --assemble /dev/md0
```

To check the MBR for grub use dd to copy the first 512 bytes of the drive (not the partition) to a file and check the file for the word "GRUB"
```
sudo dd if=/dev/sde of=MBRsde.bin bs=512 count=1
sudo dd if=/dev/sdf of=MBRsdf.bin bs=512 count=1
sudo hexdump -Cv MBRsde.bin |less
sudo hexdump -Cv MBRsdf.bin |less
```

Note that after issuing the sudo hexdump... command you can scroll through the file and look at the right hand ASCII column for text.  Near the end of the file you should see "GRUB .Geom.Hard Disk.Error" or some such.  You could also just grep for "GRUB":
```
cat MBRSDE.bin |grep "GRUB"
```
and look for the output:
```
Binary file (standard input) matches
```

That would indicate a very high likelyhood that the MBR has GRUB code in it.  

If one of the mirrors is missing the GRUB code (and one of mine was) then you have to install it manually using grub-install.  First I have to make sure /dev/md0 is assembled and mounted as /boot :
```
sudo mount /dev/md0 /boot
```

Then I can use grub-install
```
sudo grub-install /dev/sdf
```

and recheck the MBR using dd and hexdump as noted above.  

I hope this answers your questions.  It certainly helped me as I had not checked to see if GRUB was in the MBR on both of my /boot mirrors.  

The only mystery for me was why my /boot partition was not being automatically mounted.  However I may have sacculized it when I was mucking about with partitions before I realized that the drive letters were different between the partitioning program on the live DVD and the server installation I was booting.  

[Click here for the site that describes the dd trick to check the MBR if you want more details:]("http://www.geocities.com/thestarman3/asm/mbr/GRUB.htm")

Max L.

---

### Post by rgotten on 2008-05-07
> **luptonma said:**
> rgotten:


Then you can use diff to compare the two directories recursively:
```
diff -r /mnt/boot1 /mnt/boot2
```



Thnaks for your information which i am folloiwng at the present moment. In my case i am using the 3 devices for boot in raid 1..the letters will be sda1, sdb1, sdc1. I has use this for your first part of the instructions with no problem, but in the above command how should i do this???

> **luptonma said:**
> rgotten:

To check the MBR for grub use dd to copy the first 512 bytes of the drive (not the partition) to a file and check the file for the word "GRUB"

Code:
sudo dd if=/dev/sde of=MBRsde.bin bs=512 count=1
sudo dd if=/dev/sdf of=MBRsdf.bin bs=512 count=1
sudo hexdump -Cv MBRsde.bin |less
sudo hexdump -Cv MBRsdf.bin |less



I have check each of the files and all of them has the wording "GRUB .Geom.Hard Disk.Error". Now that i ha ve check them nd the files are there, how do i delete them (the files i just create to check that grub was installed). 




rgotten

---

### Post by luptonma on 2008-05-13
rgotten:

if you have sda1, sdb1 and sdc1 as RAID 1 on device /dev/md0 then you just need to stop /dev/md0 and mount the directories under /mnt.  First you need to create mount points under /mnt using mkdir.  These can be named anything but I chose boot1, boot2 and boot3:

```
sudo mdadm --stop /dev/md0
sudo mkdir /mnt/boot1
sudo mkdir /mnt/boot2
sudo mount -t ext3 /dev/sda1 /mnt/boot1
sudo mount -t ext3 /dev/sdb1 /mnt/boot2
sudo mount -t ext3 /dev/sdc1 /mnt/boot3
```

Then you can compare boot 1 to boot 2 and boot 2 to boot 3 to insure they all contain the same files.  If one is different then restart the array and fail that partition then add it back and the RAID software will rebuild it as a mirror of the others.  

Compare boot1, boot2 and boot3:
```
diff -r /mnt/boot1 /mnt/boot2
diff -r /mnt/boot3 /mnt/boot2
```

Assemble array then remove and rebuild boot3 (/dev/sdc1):
[CODE]sudo mdadm --assemble /dev/md0
sudo mdadm --fail /dev/md0 /dev/sdc1
sudo mdadm --add /dev/md0 /dev/sdc1[CODE]

If you are going to use RAID arrays you should really test the array to make sure you can fail then add a partition back in successfully otherwise the array will do you no good when a disk really fails.  I believe with RAID 1 the partitions must have the same number of cylinders, blocks or sectors.  Note that fdisk partitions by cylinders and for large disks a cylinder generally consists of 63 sectors times 255 heads = 16065 blocks and a block is 512 bytes so a cylinder is 16065 * 512 = 8,225,280 bytes at least for "large" hard drives.  

Max L

---

### Post by rgotten on 2008-05-14
Thanks for all your instructions, they have being excelent. 
What do you mean when you write [code] on the commands. 
Also in refernece to testing the RAID, i have zero one of the har drive and rebuild and works beatifull. 


rgotten

---

### Post by lokiset on 2008-05-16
I'm sure he was trying to put the stuff between the ```
 marks in a code box but missed a / in the second [code]

this 

Assemble array then remove and rebuild boot3 (/dev/sdc1):
[code]sudo mdadm --assemble /dev/md0
sudo mdadm --fail /dev/md0 /dev/sdc1
sudo mdadm --add /dev/md0 /dev/sdc1[code]

should look like

Assemble array then remove and rebuild boot3 (/dev/sdc1):
[code]sudo mdadm --assemble /dev/md0
sudo mdadm --fail /dev/md0 /dev/sdc1
sudo mdadm --add /dev/md0 /dev/sdc1
```

---

