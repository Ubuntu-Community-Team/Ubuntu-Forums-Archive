---
title: "Installing Ubuntu... some questions"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Tosh3457 on 2008-03-23
Hi, I want to install Ubuntu but I don't know how to make a new partition (I'm running windows) and I don't know if I should make the new partition running windows or ubuntu live-CD.

Also, when I make a new partition, can I choose the hard drive space I want for it? And when I save something on Ubuntu, the only partition I can save in is the ubuntu's partition?

Thanks

---

### Post by Pumalite on 2008-03-23
XP? or Vista?

---

### Post by Tosh3457 on 2008-03-23
Xp Sp2

---

### Post by Ub1476 on 2008-03-23
Start the installation procedure, and when you come to the partition section, you can resize the Windows partition to your liking. Just make sure you doesn't give Ubuntu more space than Windows already use.

Or you can download the beta of Ubuntu 8.04 (to be released 22.04.08 I think), which enables you to install it within Windows. Even though performance and such is better if you create an own partition for Linux, it's recommended to install it within Windows if you're unsure on how to resize your partition. 

Note that Ubuntu 8.04 is in beta stage, and a few things is not yet finished.

---

### Post by Pumalite on 2008-03-23
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP and choose 'resize' from the menu. Here you can decide how much you give to Ubuntu. I'd use at least 20 GB Make 3 'New' partitions in this new space:
10 GB for '/'
1 GB for /swap (in laptops /swap=RAM if you want hibernation)
The rest for /home.
Then install Ubuntu, go 'Manual' and choose the partitions already prepared, then press 'Forward'
You can read and write to ntfs in Ubuntu, so you can save files in Windows if you want.

---

### Post by gfg on 2008-03-23
> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP and choose 'resize' from the menu. Here you can decide how much you give to Ubuntu. I'd use at least 20 GB Make 3 'New' partitions in this new space:
10 GB for '/'
1 GB for /swap (in laptops /swap=RAM if you want hibernation)
The rest for /home.
Then install Ubuntu, go 'Manual' and choose the partitions already prepared, then press 'Forward'
You can read and write to ntfs in Ubuntu, so you can save files in Windows if you want.

Is  there any reason why he should use the gparted live cd instead of using the gparted already supplied on the ubuntu live cd?

---

### Post by Pumalite on 2008-03-23
The Gparted Live CD is a newer version, more powerful, more flexible and offers more control. It assures you too that you are working with unmounted partitions.

---

### Post by gfg on 2008-03-23
> **Pumalite said:**
> The Gparted Live CD is a newer version, more powerful, more flexible and offers more control.
Good to know. I will keep that in mind in the future.

---

