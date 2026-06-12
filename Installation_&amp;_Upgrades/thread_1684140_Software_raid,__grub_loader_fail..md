---
title: "Software raid,  grub loader fail."
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by derr12 on 2011-02-08
Hello, I am installing ubuntu server 10.04 with a non-standard partition setup.  This is going to be a plesk webserver so i need software mirrors.   On the suggestion of a linux geek i have setup my partions like so.

md0
200mb ext4 /boot

md1
[FONT=Courier]LVM physical volume that spans the full size of the RAID 1 device[/FONT] (2tb)  

and then i have several LVM groups for 
/ ext4
/tmp ext4
/swap 
/var ext4

when i get to the grub boot loader part of the install, it fails on the default master boot record location (obviously because of the non-standard setup)

So i tried using the location "/dev/md0"  and that does not work either.   it just craps out when it tries to install. 

any suggestions for getting the boot loader to run on a sofware raid device?

---

### Post by derr12 on 2011-02-08
from what i read, I understand that the standard setup would have me have 2 identical boot loaders on the seperate drives on non-raded partitions.

Is there no way to have a mirrored boot partition?  

My linux geek says he has this working in centOS.

---

### Post by derr12 on 2011-02-10
bump

---

### Post by derr12 on 2011-02-10
found another thread with the answer.

So it's passing the grub installer now.  I needed to add a [COLOR=black][FONT=Verdana]1mb  "reserved for boot bios"[/FONT][/COLOR] partition at the beginning of each drive.

I  guess it would have done so if i didnt use the manual partitioner and let it  setup itself.  

so there is 2 1mb boot partions and 1 raid device  with a 128mb /boot mounted partiton.

I guess thats what it takes to float  ubuntu's boat.

---

### Post by gear-dog on 2011-02-22
I've tried getting it to work pushing a dozen times now.  I should have made a spreadsheet for the combinations I've tried.


so ..  You made a 128 MB raid array for /boot, and made two little 1MB boot partitions.

Did you mount the two itty bitty partitions or are they accessed by a lower layer without the need?
If you mounted them, where?       /???
How were they configured?
Did you install grub on the small ones or the raid array?  something like "/dev/sda1 /dev/sdb1" or "/dev/md0" ?
or did you use the default grub syntax "/dev/sda /dev/sdb"


It seems to me the /boot array is superfluous as ubuntu's default is just  [/ & swap] partitions ... 

If grub is on the two 1mb partitions, whats on /boot?




maybe post that link?   =)

---

### Post by derr12 on 2011-02-23
This was all done in the Ubuntu 10.04 installation.  In the partitioning stage.   

I basically set up both disks as follows.

1mb beginning of drive, set to [COLOR=black][FONT=Verdana]"reserved for boot bios"
128mb set to physical volume for Raid
2tb rest of drive,  [/FONT][/COLOR][COLOR=black][FONT=Verdana]set to physical volume for Raid

I then created a raid 1 array "md0"  with the two 128mb partitions.  
I set the md0 device to use ext4 and set it to mount @ /boot.
Im not sure what the 1mb partition is for, but i think grub needs more than 1mb.

created "md1"  out of the big 2tb partition. 

created logical volume group on that partition and logical volumes;

/swap 16gb
/ 30gb
/tmp 1gb
[/FONT][/COLOR][COLOR=black][FONT=Verdana]/var = the rest. 


The installer setup perfectly after that. and it would boot on either drive.  

I was trying to simulate a raid failure tho and ended up deleting data off both disks....  stupid 5 bay rack had the cables crossed. thought sda was sdc.  oops.  have to re-do it tomorrow.
[/FONT][/COLOR]

---

### Post by derr12 on 2011-02-23
Im not sure where i found that post, but i found it via Google...  sorry i didn't bookmark it.

---

### Post by YesWeCan on 2011-02-23
Curious. Grub can boot a RAID 1 directly. So during the Ubuntu install you just make the big RAID 1 and LVM partitions and that should be it.

---

### Post by towheedm on 2011-02-23
> **YesWeCan said:**
> Curious. Grub can boot a RAID 1 directly. So during the Ubuntu install you just make the big RAID 1 and LVM partitions and that should be it.

Not sure it's that simple though.  I've been trying to do just that since Saturday.  Lost my saved Karmic, trashed my Windows drive MBR, thanks to Maverick changing the bootloader device everytime to select a partition.

So now I've decided to stay with Maverick, booting of a single /boot partition in sdb1 with the rest of my drive set to raid 0.  Once I set my two boot partitions on sdb1 and sdc1 to raid1, the boot fails to the grub rescue prompt saying cannot get CHS values.

There's a post around with a workaround for though.  Will try it some other time, after I've gotten this frustration thing out of my head.

---

### Post by YesWeCan on 2011-02-23
Not good.
I installed my RAID10 with a separate RAID1 for /boot, all using the alternate CD partitioner and it just worked.

I assume you did update-initramfs, update-grub and grub-install on both MBRs?
I dont know what that helpful grub error means.

---

### Post by towheedm on 2011-02-24
Gues CHS is the Cylinder/Head/Sector geometry of the drive.  I also installed from the alternate CD.  I'll try setting sdb1 as a degraded RAID1, copy /boot to sdc1, do the update stuffs, add the missing drive and see what happens.

---

### Post by derr12 on 2011-02-28
Does anybody know what is actually in that 1mb [COLOR=black][FONT=Verdana]"reserved for boot bios" partitions?  

Ive been calling them my "secret sauce" boot partitions.  

I know they are nessicary to boot from that drive, because when i broke my array, and rebuilt it on a new disk, it wouldnt boot from the new one without first doing: [/FONT][/COLOR]"cp /dev/sda1 /dev/sdb1" 

Then it booted fine.

---

