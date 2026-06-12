---
title: "partitioning problem &quot;Access is denied&quot;"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by el7azeen on 2008-10-09
Hi all

I want to partition my hard disk

whenever I ask Vista to shrink its partition, it gives me this message error "Access is denied" from Logical Disk Manager

At the beginning it only gave me 2 GB to the new partition, and when I shrink, it makes the new partition.

After I have disabled pagefiles and deleted hibernation files,
it gives me 13 GB but it can't make a new partition

access is denied

I have administrative user account, actually it's the only user account


I have a toshipa satellite A135 with 110 GB hard-dis, Vista Home Premium

I want to have install Ubuntu on the new partition

---

### Post by el7azeen on 2008-10-09
I searched all over the forums and can't get any something related to this problem.

any help plz?

---

### Post by cariboo on 2008-10-10
Usually it is recommended to defrag your hard drive at least twice before trying to resize your partition. Vista seems to have a problem resizing the partition. Have you tried using the LiveCD to resize your it. Before trying anything make sure you have backed up all your important information.

Jim

---

### Post by el7azeen on 2008-10-10
I've already defragmented the hard disk so many times, and i had the space I need to install Ubuntu. It just that Vista won't shrink.

I have tried the LiveCD the partition tool, when I choose the hard disk the slider won't move, I can't move it.

thank you for your reply

---

### Post by el7azeen on 2008-10-10
here is an attachment of a screenshot of Gparted, I can't move the slider

---

### Post by Pumalite on 2008-10-10
Have you tried disabling PageFile in Vista prior to shrinking it?

---

### Post by rishabh on 2008-10-10
I don't think Ubuntu can do it because Vista does some "bitlocker encryption" or some such thing to the filesystem.
I think you get administrator privileges if you boot Vista in safe mode, so you can edit the partitions there.

---

### Post by el7azeen on 2008-10-10
Pumalite,

I've already disabled pagefiles. at the beginning it allowed me to partition the hard disk with 2 gigabytes only, and I succeeded in doing that, then i extend the first partition to have one partition again. 

after disabling both hibernation and pagefiles, it gives me 11 gigabytes to partition, but when I ask vista to do the partitioning process, it gives me an error message "Access is denied"

rishabh,

I've done that with no success, it gives the same error message "Access is denied"

my problem is not having limited space, I've already worked that out.
my problem is how i can get out of this message "Access is denied" and have my hard-disk partitioned

thank you for ur rplies

---

### Post by Pumalite on 2008-10-10
If you can boot a Live CD; post:
sudo fdisk -lu

---

### Post by WWSmith36 on 2008-10-10
> here is an attachment of a screenshot of Gparted, I can't move the slider

In that screenshot it looks like the partition is mounted.  Gparted will only work on unmounted partitions.

I also suggest to try to get the Vista disk manager to do the shrink by safe-mode.  It may freak out Vista and cause some boot problem is gparted does something Vista doesn´t like.

Hope that helps

---

