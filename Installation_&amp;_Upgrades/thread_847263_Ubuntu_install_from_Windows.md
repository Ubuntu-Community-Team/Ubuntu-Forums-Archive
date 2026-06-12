---
title: "Ubuntu install from Windows"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by esullivan on 2008-07-02
I installed Ubuntu from Windows and LOVE it.  I am going to uninstall stuff from Windows and use it only for games and such.  

When I did the install it asked me for a disk size for Ubuntu and I set it for 15GB.  Any way to increase that now that I may need more?

Also is that install any different that, say install boot from CD?

---

### Post by Pumalite on 2008-07-02
I think you would be happier with a real dual boot:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by ForksHolder on 2008-07-02
> **esullivan said:**
> Any way to increase that now that I may need more?

Yes, There is.

But, This could be VERY dangerous and may make your windows/linux unbootable, something that will make you reinstall everything.

So, if you do that anyway, BACKUP everything you need!

---

### Post by ForksHolder on 2008-07-02
I would recomend on Gparted.

You can edit the partitions from Linux, but i would STRONGLY recogmend to do this stuff from a CD boot.

You can download it here:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)


**And remember, BACKUP the thing you need!**

Good luck :)
~ForksHolder.

---

### Post by esullivan on 2008-07-02
> **Pumalite said:**
> I think you would be happier with a real dual boot:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

Is there a HUGE difference in performance?  I don't really want to reinstall (I have setting I don't wanna redo)

---

### Post by avtolle on 2008-07-02
Look at this on the resize question: [https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

I'd also recommend you take a look at the Wubi Forum for additional information.

---

### Post by Pumalite on 2008-07-02
You are going to have to backup everything anyway. Resizing is not to be taken lightly.

---

### Post by esullivan on 2008-07-02
Maybe I just will reinstalled both OS's then, like a bandaid REALLY QUICK!

---

### Post by esullivan on 2008-07-02
If I only format part of the drive for Vista, I can just install Ubuntu on the other part right?  Ubuntu will do the duel boot settings for me?

---

### Post by avtolle on 2008-07-02
Use the Vista application to resize the Vista partition, with the remaining space on the HDD unallocated. Then, the installation disk for Ubuntu should take care of partitioning this space, installing the O/S, and setting up grub.

EDIT: Brain cramp. Before doing anything with resizing, etc., I recommend defragging the entire HDD (two times is better, three is even better). Makes things go smoother, I have found.

---

### Post by esullivan on 2008-07-02
I am just going to re-install both.  So I am going to delete the NTFS partition and format half NTFS and install Vista to it.  Then pop in the Ubuntu disk and format the other half for Ubuntu.

Ubuntu install will handle the dual boot right?

---

### Post by avtolle on 2008-07-02
Yes, it should (always has for me). Good luck.

---

### Post by esullivan on 2008-07-02
> **avtolle said:**
> Yes, it should (always has for me). Good luck.

Thanks!!

---

