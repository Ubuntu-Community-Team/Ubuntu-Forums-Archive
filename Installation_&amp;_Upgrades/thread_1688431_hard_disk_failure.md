---
title: "hard disk failure"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Homunculi on 2011-02-15
help  

after my upgrades i noticed one hard drive  was acting funny i was gonna reformat the drive anyway to totally remove winblows from my system   
grub was installed on the boot sector of the drive that failed  how can i get the next drive in line to boot  if some one can get me to a howto or tell me what i need to do short there of reinstalling  the operating system  

thanks

---

### Post by psusi on 2011-02-15
What makes you think the other drive has anything on it that can be booted?  If you remove the first disk, then your bios should use the other one.  Also there is usually an option when booting like press F12 to choose boot device, or go into the bios setup and you can usually set the boot order.

---

### Post by tgalati4 on 2011-02-15
You would need to install grub to the boot sector of the second drive.  You may or may not want to move it on the ribbon cable (if it's IDE).  Find an Ubuntu LiveCD and boot from it.  There are several posts on reinstalling grub in the forums.

---

### Post by Homunculi on 2011-02-15
drive 1 sata wd250gb  (failed) 
drive 2 sata wd320gb   ubuntu 
drive 3 sata sgt320gb  storage 
drive 4 plextor dvddl
drive 5 pioneer dvddl
drive 6 sony dvddl

i left the wd250gb on there and winblows installed on it if i needed windows i have not booted to it in 4 years now cause i like the linux system 

post me the link  or direct me to the how too ... 
ty ty 

rock on :guitar:

---

### Post by Homunculi on 2011-02-16
ok i do not know what to do now ... i booted from a live cd  .. even tried the util supergrub  .. 

the /home partition says unknown  i need 2 files out of there if anyone has a idea as to how to get on there .. cause mount will not let me in 
i can read the root  and the /usr/local partition 


[ 4318.423386] VFS: Can't find a valid FAT filesystem on dev sdb3.
[ 4318.423723] qnx4: wrong fsid in superblock.
[ 4371.719318] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
[ 5044.269368] VFS: Can't find ext3 filesystem on dev sdb3.


is my information lost ?  i just need one file out of there 
or is there a util i can get the information i need out .... 

some one please let me know  ... thanks

---

### Post by Homunculi on 2011-02-17
thanks for the ideas and the help 

i got my information off the partition ... just needed to do a little digging 

the programs i used  were supergrub testdisk and fsck 
supergrub was able to boot my root partition to a terminal where i was able to run testdisk on the drive to check the integrity of the drive and partition table... 
after seeing a invalid superblock for the /home partition  and fdisk -l listed the partition as a linux drive  i rebooted under the live cd  for 10.04 

i ran fsck against the partition that was corrupted ... it renamed all my files to #xxxxxx for the sector blocks they were in 

from a terminal i mounted the partition to view the contents of the partition 
then used sudo nautilus  to copy the files i need out to a cd-r
and recovered all my payroll information and spreadsheets for the stores ...(needless to say i will be backing them up to a flash drive more often now) 

was able to get lucid installed back and running 
with no data loss 

thanks again for any and all help 

rock on :guitar:

---

