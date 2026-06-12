---
title: "Upgraded from 9.10 to 10.04 and it appears the following."
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by jorgeluisj110 on 2010-09-18
Hello!

I've just upgraded from 9.10 to 10.04. When the laptop starts and after it runs ubuntu, the following error appears : "mount: mounting none on /dev failed: no such device". After that, a strange screen is displayed and finally the desktop appears.

The current fstab configuration is:
[I]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation
UUID=afce118e-e09f-4077-ae58-c0ac1495d63d /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation
UUID=141a3b85-6e7b-4bf8-959a-f4548ccbdc09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# Windows Partition
#/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

# UUID=C131-9AAB /storage vfat defaults 0 0

# Data Partition
UUID=C131-9AAB  /media/data  vfat  auto,users,uid=1000,gid=100,dmask=027,fmask=137 0  0[/I]

How can I fix it?

Thank you so much and I'll be waiting for your help!

---

### Post by mörgæs on 2010-09-19
I am not sure that I understand this. Are you saying that the normal desktop appears after the error message?

---

### Post by jorgeluisj110 on 2010-09-19
Yes, the normal desktop appears. Earlier this morning, I modified the grub.cfg to add the new kernel. Now, when the laptop starts and I choose Ubuntu, a black screen is shown for at least 5 seconds and then it appears the Ubuntu loading bar (it looks strange and I think there's some issue with it). 
Now, I think the error has disappeared but I'd like to know if that black screen during 5 seconds approximately is normal, I don't think so. Before I upgraded to 10.04, the 9.10 started normally and it didn't show any black screen.
I appreciate your help.
Thank you so much.

---

### Post by mörgæs on 2010-09-19
I can not give an exact answer to that, sorry. The non-exact answer would be to try a fresh install and see if it works better.

---

