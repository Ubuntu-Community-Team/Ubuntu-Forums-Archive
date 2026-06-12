---
title: "Access fstab at boot system"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by marcusbrunus on 2009-11-23
On Ubuntu 9.10 installed dual boot Windows XP via Wubi I applied manually changes to fstab file to mount windows partitions
Due certainly to mistakes I can't any more boot Ubuntu (message : kernel panic unable to mount root fs) in two modes.
Is it possible to access the fstab file to remove the bad lines at 
boot system ?
If somebody has the solution 
Thanks
Marcusbrunus

---

### Post by lemming465 on 2009-11-24
Yes.  Boot a live CD, mount the root partition, and edit your etc/fstab file.  For a WUBI install this is a two stage process.  First you have to mount the NTFS windows partition, and then you have to loopback mount the ubuntu filesystem.  Assuming windows is on sda2, and WUBI put the disk partition image files into C:\Ubuntu\disks, this could look like```

sudo -i
mkdir /media/a2
mount -t ntfs /dev/sda2 /media/a2
cd /media/a2/Ubuntu/disks
mkdir /media/root
mount -o loop root.disk /media/root
cd /media/root/etc
nano fstab
sync
cd /
umount /media/root
umount /media/a2
```

Adjust the pathnames if your partitions and files are different.

---

### Post by marcusbrunus on 2009-11-27
Hello 

Thanks for the solution. I think it was impossible
I tried the solution first with "SystemRescueCD" a good tool for recovery, but i can't resolve the right for "root" to modify the fstab file
Your solution works well
Best regards
Marcusbrunus

---

