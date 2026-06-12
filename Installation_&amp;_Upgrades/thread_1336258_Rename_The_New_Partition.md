---
title: "Rename The New Partition"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by khirodpatra on 2009-11-24
Hi

At the time of installation UBUNTU 9.04 ,I just create 4 partition from 80GB hdd

i.e 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080        9729    29318625    5  Extended
/dev/sda5            6080        7903    14651248+  83  Linux
/dev/sda6            7904        9362    11719386   83  Linux
/dev/sda7            9363        9729     2947896   82  Linux swap / Solaris


/dev/sda5 is mounted automatically after boot as lost+found in /boot
/dev/sda6 is mounted automatically after boot as lost+found in /home

I need to do all the below task please Help me out

1)Rename lost+found
2)I need to mount both the partition to be mount from /mnt after login to the system automatically.


*****************

fstab file on my machine is given below,but there is no option like 
/boot/lost+found

 /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=07089549-feea-46e9-b7eb-6e5ee7c68e0d /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=a8fb0d64-6d87-4335-9e42-025d06d9c562 /boot           ext3    relatime        0       2
# /home was on /dev/sda5 during installation
UUID=f79bea7d-099c-4615-9a23-cdc51b7b6d83 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=56d1eefd-3268-44c1-8722-8f649b5710c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Regards
Khirod Patra

---

### Post by samigina on 2009-11-24
You can do that with the Disk Utility (Palimpsest) in System/Admin menu.

---

### Post by oldfred on 2009-11-24
When you mount a new partition it automatically creates a lost+found directory as a place to put the trash. They are partitions /boot and /home per your fstab.
You can use mkdir to create additional directories with in the partition.

---

### Post by khirodpatra on 2009-11-24
1) I want to rename lost+found
2)And Both the partition to be mount from /mnt

Please Help

---

### Post by presence1960 on 2009-11-24
> **khirodpatra said:**
> 1) I want to rename lost+found
2)And Both the partition to be mount from /mnt

Please Help
why do you want to rename lost+found?

Let's see exactly what you got, do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

