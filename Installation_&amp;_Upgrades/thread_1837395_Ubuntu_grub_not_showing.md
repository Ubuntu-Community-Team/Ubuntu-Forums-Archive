---
title: "Ubuntu grub not showing"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by magnetpest2k7 on 2011-09-01
Hello all,

I have windows 7 installed in sda3 which is the primary partition and it is in c drive. I installed Ubuntu 11.04 in sda7 and selected the option to place the grub in sda7 while installing. But now the grub does not show up while booting up and the system just boots into windows 7. 

Can any one tell me how to solve this problem.

Thanks
Vin

---

### Post by ajgreeny on 2011-09-01
Grub is best put on to the root of the disk, ie /dev/sda, not onto a partition such as /dev/sda7.  I believe it is possible to leave grub on a partition, but it requires a lot more work to boot that way, and frankly, it is not worth the hassle.

I suggest you use [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) which will tell you at section 13 how to restore grub to /dev/sda.

---

### Post by YesWeCan on 2011-09-01
You have two problems. Grub2 is not reliable when installed to a partition and the normal MBR boot code will not boot a logical partition.
So I agree with ajgreeny.
If the Ubuntu root is sda7 then you need to boot a live CD and do
```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This will replace your Windows MBR boot code with Grub's. This is usually ok unless Windows decides to repair it or if you should delete the Ubuntu partition for any reason. Grub depends upon files in /boot/grub.

---

