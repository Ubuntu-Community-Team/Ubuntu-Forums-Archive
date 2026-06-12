---
title: "Swapping Partitions Around"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by MISIIM on 2010-05-06
After installing 10.04 I realized that I made a mistake while installing. I accidentally selected the wrong partition for my system partition. This means I ended up with a 40GB partition for /home. At this point I have < 1GB left and would appreciate any ideas. I would perfer not to have to reinstall.

---

### Post by ronparent on 2010-05-06
Do you have room to resize a partition?

---

### Post by MISIIM on 2010-05-06
No, it is followed by my system partition.

---

### Post by ronparent on 2010-05-06
Do you have room to resize any partition anywhere? If so you could use gparted from a live CD to copy your current 10.94 partition to an unallocated space on any drive large enough to expand it! When the copy is verified the old one can be deleted. Since grub finds the target by uuid it matters litle where it is located. You will probably have to resetup grub so grub itself is found on boot.

---

### Post by ronparent on 2010-05-06
Do you have room to resize any partition anywhere? If so you could use gparted from a live CD to copy your current 10.94 partition to an unallocated space on any drive large enough to expand it! When the copy is verified the old one can be deleted. Since grub finds the target by uuid it matters litle where it is located. You will probably have to resetup grub so grub itself is found on boot.

---

### Post by ronparent on 2010-05-06
Do you have room to resize any partition anywhere? If so you could use gparted from a live CD to copy your current 10.94 partition to an unallocated space on any drive large enough to expand it! When the copy is verified the old one can be deleted. Since grub finds the target by uuid it matters litle where it is located. You will probably have to resetup grub so grub itself is found on boot.

---

### Post by ronparent on 2010-05-06
Do you have room to resize any partition anywhere? If so you could use gparted from a live CD to copy your current 10.94 partition to an unallocated space on any drive large enough to expand it! When the copy is verified the old one can be deleted. Since grub finds the target by uuid it matters litle where it is located. You will probably have to resetup grub so grub itself is found on boot.

---

### Post by ronparent on 2010-05-06
Do you have room to resize any partition anywhere? If so you could use gparted from a live CD to copy your current 10.94 partition to an unallocated space on any drive large enough to expand it! When the copy is verified the old one can be deleted. Since grub finds the target by uuid it matters litle where it is located. You will probably have to resetup grub so grub itself is found on boot.

---

### Post by MISIIM on 2010-05-07
Well, I don't really have any unallocated space. I'll just reinstall some time soon.

---

### Post by dino99 on 2010-05-07
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

