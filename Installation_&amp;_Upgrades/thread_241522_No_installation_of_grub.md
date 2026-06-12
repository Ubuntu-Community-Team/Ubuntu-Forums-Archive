---
title: "No installation of grub?"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by shunkk on 2006-08-22
Hello, I've some troubles to the installation of ubuntu 6.06 LTS. My apologies for my english first :oops: , but at my language forum and the irc channel I don´t get any help at all :/.

I create the partitions, and install, the installation goes well except for the update of security, beside this, the install is pretty easy, my congrutulations to who made that possible ;). But when the OS reboot, grubs don't shows up, the system loading windows just like ubuntu didn't exist. 

This happen to me in the version 5.10, but only after i put a second hard disc on my computer. I Have two hard drives one SATAII where i put windows and the second SATA where i put all my files. 

I test the installation in boths hard disc, in both happend the same, just load windows...

If you need to know more information please let me know.

Thanks for your time

Regards.

---

### Post by Original Brownster on 2006-08-22
Hi,

> **shunkk said:**
> 
I create the partitions, and install, the installation goes well except for the update of security, beside this, the install is pretty easy, my congrutulations to who made that possible ;). But when the OS reboot, grubs don't shows up, the system loading windows just like ubuntu didn't exist. 

This happen to me in the version 5.10, but only after i put a second hard disc on my computer. I Have two hard drives one SATAII where i put windows and the second SATA where i put all my files. 


Just confirm that when you installed ubuntu you chose the option to install the boot loader grub to your mbr? 
I suspect you did and it has placed it on the mbr of the 2nd hard drive.
If I am right I think all you need to do is go into the BIOS settings of your pc and change the boot order so that your 2nd hard drive is the first boot device instead of your 1st hard drive. 

Hope that makes sense, let us know how you get on.

Cheers,

---

### Post by shunkk on 2006-08-22
This is the abstract of the install screen

[[img]http://img3.freeimagehosting.net/uploads/th.fcbb0bbaed.jpg[/img]](http://img3.freeimagehosting.net/image.php?fcbb0bbaed.jpg)

Sorry it's in spanish.

I try the installation in boths hard discs, in one of them should be work, but is not.

I have the doubt i have the table of partitions screen I only select the partitión to linux and de partition to swap, but i didn't touch the partition 'of Windows', i should be select in this one the /boot option?

I'll try again and I'll take some photos for you can understand me better.

Thank you.

---

