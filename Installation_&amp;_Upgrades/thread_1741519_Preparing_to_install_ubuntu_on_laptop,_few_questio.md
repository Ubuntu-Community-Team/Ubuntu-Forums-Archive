---
title: "Preparing to install ubuntu on laptop, few questions"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Jorrit Tjarks on 2011-04-28
hello, 

Ive been using Ubuntu for some years now and decided to install the OS on my laptop as well next to the delivered windows 7 installation. Its a acer laptop with 2 hidden primary partitions, these partitions probably contain the windows installation images. 

The way the drives are setup now are:

Partition | file system | label           | size   | Flags |

/dev/sda1 | ntfs        | PQservice       | 14  GiB| diag  |
/dev/sda2 | ntfs        | system reserved | 100 MiB| boot  |
/dev/sda3 | ntfs        | Acer            | 48  GiB|       |
/dev/sda4 | ntfs        |                 | 240 GiB|       |

the windows installation is on the sda 3 partition called acer. My data is on the sda4 240 GB partition. No idea whats on the sda 1 and sda 2.

ideally i want to resize the sda 4 partition to make room for a 40 gb Ubuntu installation partition. 
however because there are already 4 primary partitions so i have to delete one and make a extended partition. 

My idea was to delete the data partition and divide it into 3 separate partitions. 1 for my data 1 for the Ubuntu installation and one for swap. 

now my question is: is it possible to install a Ubuntu system on a extended partition? and is it recommended. Or how would you setup the drives?

I would love to remove these stupid hidden acer partitions. however i don't want to lose my win 7 re-installation option.

Jorrit

---

### Post by Lateralis on 2011-04-28
It is possible to install Ubuntu in an extended partition - that's what I've done on my laptop.  Ubuntu frankly doesn't care where it is installed, so you can install it anywhere you like.  On my laptop, the first partition is the Windows Recovery, second is Vista (Yeuch!), third is a data partition which contains everything I need to share between Vista and Ubuntu and then the fourth is an extended partition which contains my Ubuntu installation. 

I agree with you though - don't tamper with the first three.  I would personally backup to an external medium, e.g. DVDs or external hard drive, the whole of data partition and any important files in your Windows System partition, then use the in built Windows tools to delete the data partition.  From there, boot into the Ubuntu LiveCD and use GParted to make all of the partitions you need to install Ubuntu.  Then, restore all of your data from your backups to your newly created data partition within the extended partition.

---

### Post by Jorrit Tjarks on 2011-04-28
Thank you Lateralis, thats all the information i needed.

Jorrit

---

### Post by Mark Phelps on 2011-04-28
BEFORE you do anything else, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  You might need this later to repair the Win7 boot loader.  Without it, your Win7 OS would then be unbootable.

Also, when doing the paritioning in Disk Management, if it offers to change the "drives" to "dynamic" -- make sure you do NOT allow it to do so.  That should not happen in your case, just wanted to make you aware of it.

---

