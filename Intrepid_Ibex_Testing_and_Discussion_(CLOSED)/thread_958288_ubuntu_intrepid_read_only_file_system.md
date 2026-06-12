---
title: "ubuntu intrepid read only file system"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by trigsenior on 2008-10-25
Hello upgraded from hardy to intrepid.

When i try to boot it seem to boot me into read only file system.

*starting ACPI services
acpi: can't open Socket /var/run/acpid.read only file system.

get several more read only file sytem errors. Then just logs me into tty.

I ran fsck no erros my drive is fine , had a look at /etc/fstab

/dev/sda3
UUID=719c979e-ad26-acb0-f1ac7b757911 /ext 2      relatime,erro$ 

/dev/sda1
UUID=543f23ad-e0e6-41ba-a396-546496v7244b1 none    swap sw 


fdisk
           start       End       Blocks     ID    system
/dev/sda1  1           192       1536000    82   Linux swap / Solaries
partition 1 does not end on cylinder boundary.

/dev/sda2              192       121856000 7 HPFS/NFTFS
partition 2 does not end on cylinder boundary.

/dev/sda1  15362    30401                   83           Linux

iv tried re mounting with read right permissions but impossible as read file system only. 

I can how ever boot into recovery mood, however when x starts gives me HAL error mouse keyboard dead. TTy again.

here is kernel version might be related?

uname -r

2.6.24-19-generic

Been googling around for same problem found bug report which looks bit  like my problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189)

There person with my problem is also runnign ext2 could be part of bug ?

thanks any help would be nice.

---

### Post by ibuclaw on 2008-10-25
With any upgrade, I recommend just installing a fresh new Operating System.

If you haven't set up your partitions to have a separate /home partition, then you'll have to go into LiveCD and back that data up.

As it stands at the moment though, try booting into your last good boot configuration.

If that fails, boot into a LiveCD environment and check the partitions for any errors with the Partition Manager.

Regards
Iain

---

### Post by trigsenior on 2008-10-25
hello having problem with being stuck in read only file system.

Today just upgraded from hardy to ibex.

Booted up and got read and right permission error, booted to read only. 

when booting gets stuck at acpi and turns to read only. 

Ran fsck thought was corrupt drive , drive is fine.

Tried manually mounting can't because read permission only.

had look at fdisk -l , make sure nothing weird.

/dev/sda1 1 192 1536000 82 linux swap
Partition 1 does not end on cylinder boundary.
/dev/sda2                   HPFS/NTFS 
Partition 2 does not end on cylinder boundary.
/dev/sda3                   Linux
Partition 3 does not end on cylinder boundary.

now had look at fstab

/dev/sda3 
UUID= long number                   / dev ext 2 relatime,erro$

/dev/sda1
UUID= long number                      none swap

 ( might be kernel bug like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250189))
uname - r

2.6.24-19-generic

Just discover i can boot with rw, if i go though recovery however x crashes because of HAL error ? 

many thanks , hope provided enough

---

### Post by overdrank on 2008-10-25
Please do not create multiple threads on the same issue. threads merged :)

---

### Post by ibuclaw on 2008-10-25
Thanks overdrank :)

---

### Post by trigsenior on 2008-10-25
sorry about same posts was an accident. Didn 't think it had gone though or forgot all got very confusing. 

I ve booted up live cd , save all my stuff going to try Ubuntu 8.10-rc
hopefully better luck.

---

### Post by trigsenior on 2008-10-25
how can i change permissions on live cd to copy old /home folder? i Tried sudo nautilus then permission tab 
still not allowed
** update **

You have to change permissions to all files not just /home folder

---

