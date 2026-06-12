---
title: "Linux Ubuntu Server Software raid Error"
date: 2019-07-16
forum: Installation &amp; Upgrades
---

### Post by chrispet on 2019-07-16
Hi, i have this server : HPE Proliant Dl80 gen9. My server has two Hard disk drives. I want to install the ubuntu server 18.04 Version. In installation in the Partitioning Step I chose the manual option and i made the partitions for Raid alone.[CENTER]
[/CENTER]
[TABLE="class: grid, width: 200, align: center"]
[TR]
[TD]Disk 1 : 1 TB
[LIST]
[*]984 GB ext4 /
[*]16.02 GB Swap
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Disk 2 : 1 TB
[LIST]
[*]984 GB ext4 /
[*]16.02 GB swap
[/LIST]
[/TD]
[/TR]
[/TABLE]

Then i choose the "Configure Raid" option so my new partitions after that are like that :
[TABLE="class: grid, width: 200, align: center"]
[TR]
[TD]Raid 1 : 984 GB ext4 /[/TD]
[/TR]
[TR]
[TD]Raid 2 : 16.02 GB swap[/TD]
[/TR]
[TR]
[TD]Disk 1 : 1 TB
[LIST]
[*]984 GB ext4 /
[*]16.02 GB Swap
[/LIST]
[/TD]
[/TR]
[TR]
[TD]Disk 2 : 1 TB
[LIST]
[*]984 GB ext4 /
[*]16.02 GB swap
[/LIST]
[/TD]
[/TR]
[/TABLE]

At the end of proccess i click on "finish partioning and Write settings to Disk"
The Installation begins but unfortunately after a minutes i got this error :
[IMG]https://i.stack.imgur.com/K5AF3.png[/IMG]

I tried to change a few settings such as : Disable raid controller, Change the Sata from raid to ASCHI mode and finally change the boot option from UEFI to Legacy but the error is still remaining. Please tell me what can i do for that.

---

### Post by SeijiSensei on 2019-07-16
Last I checked you can't write the boot record to a RAID array because the drivers to support mdadm are not available until the kernel is loaded. I usually write the entire root filesystem to bare metal on one of the drives, and use dd to make an identical image in a same-sized partition on the other drive as an emergency spare. I then use the rest of the drives to create a RAID1 which I mount as /home.  

So I'd set aside maybe 20 GB for / on both drives, and format the partition on the first drive as ext4. (Using dd to image the partition to the other drive makes a bit-for-bit copy and doesn't care what the filesystem is.)

---

### Post by chrispet on 2019-07-16
Hi! Because i'm newbie could you give informations for that Step by Step?

---

### Post by rsteinmetz70112 on 2019-07-17
I don't know how it worked for me but I've been able to install on  an mdadm raid array. 

You may have to run # grub-install from the command line on both sda and sdb. 

It is also possible create only one raid array on sda1 and sdb1 and have sda1 as /boot and sdb1 as swap. There is no particular reason I can think of to have swap on an raid array.

---

