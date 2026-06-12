---
title: "preseed - Partitioning Second Hard Disk"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by dsraju on 2011-06-15
My apologies if this has been asked before. I am asking after a lot of unsuccessful searching!
I setup "preseed" PXE/network automated install. It works perfectly with one hard disk (/dev/sda).
...
d-i partman-auto/disk string /dev/sdad-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto/expert_recipe string \
  boot-root :: \
    4096 200 4096 ext3 \
      $primary{ } \      $bootable{ } \
      method{ format } format{ } \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ / } \
    . \
...

Actually  I need to make it work with two disks sda and sdb "regular" (no LVM or  RAID offered by "partman") to keep /usr /var etc on sdb.
The doc /usr/share/doc/debian-installer/devel/partman-auto-recipe.txt.gz doesn't explain much on "regular" partitions.
I have tried installer both Ubuntu(amd64 server) v10.10 and v11.04 to find no difference.

If  "partman" doesn't handle second hard disk, Is there anyway that I can  run my own set of commands to partition and mount disks sda and sdb 
before the installer begins installing, (ex: places like "partman/early_command")!
ex:
d-i partman/early_command string /bin/my_partition.sh
(btw, I placed my_partition.sh in initrd)

I  also tried to partition second hard disk sdb and copy respective  folders /target/usr /target/var, fix fstab as part of the "late_command"  
but its tricky!
d-i preseed/late_command string fix_sdb.sh


I've never seen partitioning issues using Kickstart on Redhat/Fedora/Centos. So I have tried it on Ubuntu hoping
the Kickstart method fixes the issue. Interestingly it failed to take the second disk,
kickstart:
...
part /    --fstype ext3 --size 1 --grow --asprimary --ondisk=sda
part /var --fstype ext3 --size 1 --grow --asprimary --ondisk=sdb
part /usr --fstype ext3 --size 9000 --asprimary --ondisk=sdb
...
Correct me if I wrong, it appears like the Kickstart file has been parsed into preseed file by installer!

Appreciate if you have any comment on how to fix it in either preseed or Kickstart!

related links:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[http://superuser.com/questions/281518/how-can-partman-partition-more-than-one-disk-in-a-debian-installer-preseed-file](http://superuser.com/questions/281518/how-can-partman-partition-more-than-one-disk-in-a-debian-installer-preseed-file) 
[http://ubuntuforums.org/showthread.php?t=1549202&highlight=preseed+partition](http://ubuntuforums.org/showthread.php?t=1549202&highlight=preseed+partition)   [http://ubuntuforums.org/showthread.php?t=801348&highlight=preseed+partition](http://ubuntuforums.org/showthread.php?t=801348&highlight=preseed+partition)  
[http://ubuntuforums.org/showthread.php?t=1119983&highlight=preseed+partition](http://ubuntuforums.org/showthread.php?t=1119983&highlight=preseed+partition) 

-raju

---

### Post by tomh0665 on 2011-06-21
d-i partman-auto/disk string /dev/sda /dev/sdb

and then use "device { /dev/sdb }" for "/" and "/boot" and "device { /dev/sdb }" for "/usr" and "/var".

---

### Post by dsraju on 2011-06-22
Thank you tomh0665 for looking at it.
Actually I tried this as well but it didn't help.
I have tried again, here is the preseed file,
...
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto/expert_recipe string \
  boot-root :: \
    4096 200 4096 ext3 \
      $primary{ } \
      $bootable{ } \
      method{ format } format{ } \
      device{ /dev/sda }
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ / } \
    . \
    100 50 100 ext3 \
      $primary{ } \
      method{ format } format{ } \
      device{ /dev/sdb }
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ /usr } \    . \
    1250 100 1650 ext3 \
      $primary{ } \
      method{ format } format{ } \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ /sysrestore } \
    .
...

I got the following message,
"Partition disks"
"No root file system"
"No root file system is defined."
"Please correct this from the partitioning menu."
<Continue>
When I press 'Continue' it goes back to the same screen. I guess it got into a loop.
I appears that it switched to sdb and ignored the sda where the root is defined.
Hope I am not missing any!

Its kind of a surprise that Debian/Ubuntu doesn't support the 'regular' second hard drive in automatic install method.

---

### Post by dsraju on 2011-06-22
I tried an alternative approach.
run a script using late_command to create (sdb) partitions, format them and fix /target/etc/fstab accordingly and move '/target/usr/*' and '/target/var/*' to the new respective partition!

..
d-i preseed/late_command string addseconddisk.sh 
..

made sure the correctness /target/etc/fstab entries before reboot.

It gives me the following message after the reboot:
"**init: ****ureadahead main process (376) terminated with status 5"**


ref: [http://ubuntuforums.org/showthread.php?t=1423305](http://ubuntuforums.org/showthread.php?t=1423305)

---

### Post by tomh0665 on 2011-06-30
> Thank you tomh0665 for looking at it.
> Actually I tried this as well but it didn't help.

You're welcome.

Apologies about replying this late. I'd forgotten about posting here so I wasn't checking for an answer and the email letting me know that you'd replied went to spam...

AFAIK, the "No root file system" and/or "No root file system is defined" mean that the recipe's incorrect.

Looking back at the documentation, I have to apologize a THIRD time. The "device" variable is specific to an LVM preseed... :(

Googling yields that as of 2009 preseeding a multi-disk regular install. It doesn't seem right. If I have the time, I'm going to do a manual two-disk install and take a look at the equivalent pressed file that debconf-get-selections generates.

---

### Post by tomh0665 on 2011-06-30
> I tried an alternative approach.
> run a script using late_command to create (sdb) partitions,
> format them and fix /target/etc/fstab accordingly and
> move '/target/usr/*' and '/target/var/*' to the new respective
> partition!

Those two moves must lengthen the install time!

I meant to point out in my first reply, but forgot, that a separate "/usr/" might break some things (it's certainly the case in Fedora) but I had no idea that a separate "/var" is also problematic - although disabling ureadahead must solve that latter issue.

---

### Post by dsraju on 2011-07-06
> **tomh0665 said:**
> > Thank you tomh0665 for looking at it.
> Actually I tried this as well but it didn't help.

You're welcome.

Apologies about replying this late. I'd forgotten about posting here so I wasn't checking for an answer and the email letting me know that you'd replied went to spam...

AFAIK, the "No root file system" and/or "No root file system is defined" mean that the recipe's incorrect.

Looking back at the documentation, I have to apologize a THIRD time. The "device" variable is specific to an LVM preseed... :(

Googling yields that as of 2009 preseeding a multi-disk regular install. It doesn't seem right. If I have the time, I'm going to do a manual two-disk install and take a look at the equivalent pressed file that debconf-get-selections generates.
sorry that I didn't check back for the last few days!
tomh0665,
yes,I did manual install and got the debconf selection, some thing like,

...
# This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings (file system, mount point, etc.), a free space to create partitions, or a device to initialize its partition table.
# Choices: Guided partitioning, Configure software RAID, Configure the Logical Volume Manager, Configure encrypted volumes, Configure iSCSI volumes, , SCSI1 (0\,0\,0) (sda) .......395.3 MB${!TAB}${!TAB}f${!TAB}swap${!TAB}${!TAB}swap${!TAB}, SCSI5 (1\,4\,0) (sdb) -...
....
# Amount of volume group to use for guided partitioning:partman-auto-lvm        partman-auto-lvm/guided_size    string  some number
...

Well, I didn't choose either RAID or lvm!
I believe the system was forced to choose one of them when two disks are selected for different partitions!

anyway, I used the above 'Guided partitioning' in my preseed file for automatic install, to find that the system popping up a partition alert window that it is missing root partition!

---

### Post by dsraju on 2011-07-06
>"/usr/" might break some things (it's certainly the case in Fedora)
yes, I am afraid that it would run into problems and decided to leave it (/usr) on the root partition for now!
About /var, the /var/{lock,run,lib} needs to be on the root partition to get rid of the ""**init: ****ureadahead..."** error. I haven't tried to disable the ureadahead yet, not sure if it comes with ant other issues.
appreciate your time.
thanks, -raju

---

### Post by tomh0665 on 2011-07-10
> yes,I did manual install and got the debconf selection
> Well, I didn't choose either RAID or lvm!
> I believe the system was forced to choose one of them
> when two disks are selected for different partitions!
> anyway, I used the above 'Guided partitioning' in my
> preseed file for automatic install, to find that the system
> popping up a partition alert window that it is missing root
> partition!

I did a manual install and looked at the partman stanzas that are used.

I'm too busy these days to try (but I will do so eventually!) but I have a feeling that it MIGHT work if you just format "/dev/sda" (with, for example "/" and "/boot") and then format "/dev/sdb" (with "/usr" and "/var").

---

### Post by dsraju on 2011-07-17
>I'm too busy these days to try (but I will do so eventually!) but I have a feeling that it MIGHT work if you just format "/dev/sda" (with, for example "/" and "/boot") and then format "/dev/sdb" (with "/usr" and "/var").[/QUOTE]

I tries the following preseed file:
...
d-i partman-auto/disk string /dev/sda /dev/sdb
#and appended ( /dev/sdb) in later try,

d-i partman-auto/expert_recipe string \
  boot-root :: \
    6000 200 1000000 ext3 \
      $primary{ } \
      $bootable{ } \
      method{ format } format{ "/dev/sda" } \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ / } \
    . \
    2000 50 2000 ext3 \
      $primary{ } \
      method{ format } format{ "/dev/sdb"} \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ /usr } \
    . \
    1536 100 1536 ext3 \
      $primary{ } \
      method{ format } format{ "/dev/sdb" } \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ /var } \
    .
    200 60 200 linux-swap \
      method{ swap } format{ } \
    .



#### removed [COLOR=#000000][FONT=Times][FONT=verdana]curly brace[/FONT][/FONT][/COLOR] in the next try,
d-i partman-auto/expert_recipe string \
  boot-root :: \
    6000 200 1000000 ext3 \
      $primary{ } \
      $bootable{ } \
      method{ format } format "/dev/sda"  \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ / } \
    . \
    2000 50 2000 ext3 \
      $primary{ } \
      method{ format } format "/dev/sdb" \
      use_filesystem{ } filesystem{ ext3 } \
      mountpoint{ /usr } \
    . \
    1536 100 1536 ext3 \
      $primary{ } \
      method{ format } format "/dev/sdb"  \
      use_filesystem{ } filesystem{ ext3 } \      mountpoint{ /var } \
    .
    200 60 200 linux-swap \      method{ swap } format "/dev/sdb"  \
    .

After reboot:

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              7319480    837508   6110160  13% /
none                   4088680       244   4088436   1% /dev
none                   4096584         0   4096584   0% /dev/shm
none                   4096584        48   4096536   1% /var/run
none                   4096584         0   4096584   0% /var/lock
none                   7319480    837508   6110160  13% /var/lib/ureadahead/debugfs
$ 
 /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3044b0d8-2077-4194-80c7-28e0ad00654e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bebf4f56-b6b9-44dc-85c4-51b4266cf6fb none            swap    sw              0       0

The sdb partitions didn't make it. Not sure if this problem has ever been fixed at least in the later versions like 11.x.

thanks, -raju

---

### Post by shivanayak@gmail.com on 2012-01-18
Hi Raju,

I am also looking for similar solution. Were you able to partition the disks successfully with preseed? Please let me know. 
I  would like to know how did you use the Guided partition string in preseed ?

Thank you in advance.
-Shiv

---

### Post by dsraju on 2012-01-19
No.
The only solution worked for me was, move few folders like /var/log to second disk and make sym links from the first disk.

-raju

---

### Post by shivanayak@gmail.com on 2012-01-19
Than you Raju for the response.

Can you please educate me on how to use the "**Guided partition**" string shown when I used debconf-get-selectoions after answering the Ubiquity questions.

Here is what I am thinking of doing, 

1. Partition the disks before invoking the Ubiquity.
2. Use preseed to make use of the partitions already created . 
3. If I use the preseed with "expert_recipe", it is overwriting already created one. (for only one disk)

ubiquity    partman-auto/expert_recipe string             \
      boot-root ::                                            \
              1 50 10240 ext4                                  \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
              .                                               \
              64 512 8172 linux-swap                         \
                      method{ swap } format{ }                \
              .                                               \
              500 10000 30720 ext4                          \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /backup }                     \
              .                                               \
              500 10000 -1 ext4                          \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /home }                     \
              .


Any suggestion based on your experience.

Thank you .

---

