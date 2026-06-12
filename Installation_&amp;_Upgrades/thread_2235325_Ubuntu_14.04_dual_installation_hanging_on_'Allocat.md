---
title: "Ubuntu 14.04 dual installation hanging on 'Allocate drive space' screen"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by Arsemyth on 2014-07-20
Hi, 

I hope someone can help me here.

I am in the middle of installing ubuntu 14.04 onto a friend's laptop. It will be dual boot with XP Professional.  I am using a DVD which I have used to successfully install Ubuntu 14.04 on other machines.

The process has got to the point where I have configured the wireless connection, and it has asked me to select the drive and allocate drive space.  

I pressed 'continue' at around 1am this morning and it is still 'busy' (but no disc activity) now... it is almost 17.00 hours.

My question is....

Is it safe to halt the process, or will doing so bugger things up for all time?

Thanking you in advance

Roger

---

### Post by yancek on 2014-07-20
Did you select a partition on which to install?  Did you select a filesystem type as well as a mount point and did you select to format prior to clicking Continue.  If you did, the mbr may have been overwritten.

Did you check the minimum hardware requirements for Ubuntu 14.04 on this computer.  If it came with xp installed, it could be 10+ years old and may not have the capacity to run Ubuntu.

---

### Post by Arsemyth on 2014-07-20
Hi yancek, 

I selected a partition and file system type ext4, and as it is going to be dual-boot I didn't select to format the drive.  The laptop is a pretty basic configuration Acer but actually better than the Dell laptop I am currently running 14.04 on.

By the way, the acer is STILL locked on the 'Allocate drive space screen'

Rog

---

### Post by yancek on 2014-07-20
> I selected a partition and file system type ext4, and as it is going to be dual-boot I didn't select to format the drive.

I think you might be confusing partition and drive.  windows often uses drive and partition interchangeable.  If you don't format the partition you want to install Ubuntu to, I doubt it will work as you need it formatted to a Linux filesystem type.  Your windows install should be on a different partition and formatting a partition for Linux/Ubuntu should not have any effect on it, as long as you choose the correct partition and don't format a ntfs partition.

---

### Post by Arsemyth on 2014-07-21
Hi, 

I have 'solved' my problem by turning off the laptop after getting bored by it's attitude!

Result... 

It boots up into Windows XP as before with no sign of any damage from the failed Ubuntu installation (phew!)

This evening I will have another attempt!

Thanks for your input yancek!

Rog

---

### Post by yancek on 2014-07-21
The link below has a tutorial on installing Ubuntu 14.04 which is pretty detailed and includes info on partitioning,  Might be helpful to read before your next attempt.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

