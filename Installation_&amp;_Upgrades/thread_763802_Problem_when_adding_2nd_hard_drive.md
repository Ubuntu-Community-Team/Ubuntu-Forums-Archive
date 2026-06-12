---
title: "Problem when adding 2nd hard drive"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by stymie61 on 2008-04-23
I am having a problem when adding a 2nd hard drive to my computer.
It is a removable samsung 320gb HD. Problem is when I go to start up Ubuntu 8.04 from grub, I get a msg stating doing a routine disk check. Gets to sda5 and reboots. ran it in repair mode and the problem was fixed as far as doing system check but still locks up when it is hooked up. Also I cannot connect to the internet when in linux but can when unit is in XP.

 System is a Dualboot XP/ubuntu 8.04 w/ partitioned 250gb hd 1gb ram, AMD 64 3000. Motherboard is a Soyo ck8 Dragon plus. I know I have to set the sata jumpers when using 2 hd's to read master and slave.
 Any help with this would be appreciated.

BTW what I am trying to do is use this caddy to format HD's in ext2 for use in the field.

---

### Post by dstew on 2008-04-23
> I am having a problem when adding a 2nd hard drive to my computer.Regarding your drive problem, you should not have to set any jumpers for master/slave with SATA drives. I don't think the drives will have jumpers on them. And, leave the motherboard jumpers alone.> locks up when it is hooked upDoes it only lock up when you boot Ubuntu?> I cannot connect to the internet when in linux but can when unit is in XP.Is this problem related to the drive problem?

---

### Post by stymie61 on 2008-04-23
In regards to your questions:

1)Yes it only happens with Ubuntu. It shows as a disk in XP

2) I have to set sata jumpers on my motherboard (work purchased)

3) Drive has only a lost and found folder on it.

---

### Post by dstew on 2008-04-23
Without the drive plugged in, boot into Ubuntu, and post the output of```
sudo fdisk -l
cat /etc/fstab
```

---

