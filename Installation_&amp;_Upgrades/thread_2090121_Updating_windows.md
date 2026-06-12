---
title: "Updating windows"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by louisgonick on 2012-12-01
I've decided that I'll be updating to Windows 7 (a bit late, I know)on my machine. I dualboot with grub Ubuntu 12.04 and I will be doing a clean install. 

My plan was to backup all my files in the Ubuntu partition, but will completely erasing the C partition and installing a fresh new windows mess with grub or my Ubuntu partition? 

Thanks, any help is appreciated.

---

### Post by Sef on 2012-12-01
> My plan was to backup all my files in the Ubuntu partition, but will completely erasing the C partition and installing a fresh new windows mess with grub or my Ubuntu partition? 

1) Back up your oses with [Clonezilla]("http://clonezilla.org").

2) Installing Windows on the C partition should not erase Ubuntu.

3) GRUB will need to be reinstalled. Check out [Super GRUB disk]("http://http://www.supergrubdisk.org/").

---

### Post by louisgonick on 2012-12-01
> **Sef said:**
> 1) Back up your oses with [Clonezilla]("http://clonezilla.org").

2) Installing Windows on the C partition should not erase Ubuntu.

3) GRUB will need to be reinstalled. Check out [Super GRUB disk]("http://http://www.supergrubdisk.org/").

I read that installing boot-repair on a live CD will also work for fixing grub. 

Which out of the two is better?

---

### Post by dino99 on 2012-12-01
boot-repair is the easy way, and works very well  :)

---

