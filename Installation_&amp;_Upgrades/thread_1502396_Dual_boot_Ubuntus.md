---
title: "Dual boot Ubuntus"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by holocene on 2010-06-05
I would like to dedicate a new hard drive to dual booting two or more instances of Ubuntu. 

It's my understanding that grub2 can not accomodate this, so I used a legacy grub to establish MBR,  and a stage 2 file into the /boot partition. I am unclear on this point, but subsequent O/S installs will use the existing MBR, and maybe the existing /boot partition, unchanged? 

Using this as a guide: [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

I get to the point where I am at the console in the newly rebooted/installed 9.04 server, and at grub, and I get this

```
grub>find /boot/grub/stage1

Error 15: File not found. 
```What is odd is that the file does exist, though it is not executable. 

What am I doing wrong here? 

Thanks in advance
Steve. 

-----------------------------------------------------------------------------

Here is a summary of the whole exercise to date:

1. booted the 9.04 server cd.

2. manually partitioned my new disk as follows (/dev/sda)
       > partition 1 ext4 mounted as /boot with 100MB space
       partition 2 swap with 6GB space
       partition 3 ext4 mounted as / with 30gb space
       (remainder of space left unpartitioned.)3. Continued with install choosing no extra packages

4, Near the end, I recall the installation asks about booting the system. I think I followed these extracted instructions:

> Finish partitioning and write changes to disk -> "Installing the base system" -> ... -> 
->"Install the Grub boot loader to the master boot record?":  YES -> Continue 
 In this step, Grub must be installed both on the MBR (master  boot record) as well as locally on the partition being installed (in  this example /dev/sda6). The local version will be chainloaded by  the MBR version. Therefore, install Grub a second time:  -> Go Back -> Install the Grub boot loader on a hard disk ->   "Install the Grub boot loader to the master boot record?": NO -> Device for boot loader installation: /dev/sda6 -> Continue 
I recall that I did the "back" function, and then choose "write to hard drive". 

5. Removed cd disk and rebooted.

6. Ran these items on the console:

```
sudo mkdir /media/GRUBpartition
sudo mount /dev/sda1 -t ext4 /media/GRUBpartition
sudo mkdir /media/GRUBpartition/boot
sudo mkdir /media/GRUBpartition/boot/grub
sudo chmod 777 /media/GRUBpartition/boot/grub
sudo cp -r /boot/grub/* /media/GRUBpartition/boot/grub
sudo nano /media/GRUBpartition/boot/grub/menu.lst
```7. keyed this into the menu.lst (overwriting an existing file), and saved it. 
```

## ## End Default Options ##
title  first O/S (chainloader)
rootnoverify    (hd0,2)
chainloader    +1
title Second O/S for the future (chainloader)
rootnoverify   (hd0,3)
chainloader    +1
```8. Returned permissions to root
```
sudo chmod 744 /media/GRUBpartition/boot/grub
sudo chmod 744 /media/GRUBpartition/boot/grub/*
```9. At this point, after starting grub, attempt this, as per instruction link:
```
sudo grub
grub> find /boot/grub/stage1
```It fails as stated at the top.

---

### Post by kansasnoob on 2010-06-05
Read some of this:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Specifically:

> I would not recommend making a separate /boot partition for any reason than for overcoming GRUB error 18.

And:

> The main disadvantage of having to use a separate /boot partition is that is you want to dual boot more than one Linux installation, it is a bit tricky to get two or more linuxes to share the same separate /boot partition.
If you try, any files with the same name in the new system you might be installing will overwrite files belonging to your existing system and you will lose the boot of your existing Linux.

There is seldom a need for a separate /boot partition and it's absolute nonsense that grub 2 won't multi-boot more than one *buntu:

[ATTACH]159443[/ATTACH]

I'm booting all that with grub 2 and I've had even more at different times, including Debian Squeeze, Lenny, Fedora 12, etc. Grub 2 is not flawless but it's pretty darn good.

---

### Post by oldfred on 2010-06-05
I do not think you made a /boot partition even though you named it that. You have made a /grub partition. You did not copy any boot files.

Did you create a separate /boot when you installed? I agree that you do not need nor want a separate /boot especially with multiple installs. You may for server installs or raid setups or the error 18 old BIOS issue.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

Grub2 partition discussion:
[http://ubuntuforums.org/showthread.php?t=1465772](http://ubuntuforums.org/showthread.php?t=1465772)

---

