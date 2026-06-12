---
title: "Ubuntu Dual boot with XP problem?"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Ondas on 2008-04-13
Hi,
I am a new Ubuntu user, so am looking for some advice in installing a dual boot system from Windows XP.
I have searched this site and many others for instructions on how to set this up, but each guide contains the situation were Windows is  installed as a single partition on the whole disk. However my windows set up contains 2 partitions: 1 NTFS partition (100GB) and 1 Fat32 data partition (100GB). So my plan is too install ubuntu on a third of the Fat32 partition, but when running the live CD I am unsure what exactly I should be doing as I don't want to end up deleting my windows system by mistake.
 
It seems I have 2 choices,

1.Shrink the fat32 partition to around 60GB using gparted program before running installation. Then, run installation and select the "Guided -use the largest continuous free space" option, which seems fairly straight forward, and something I should be able to do I think.

2.Attempt a manual setting up of the new ubuntu partition within the installation procedure. However I have no idea how to do this, and cannot find anywhere that shows you how to do this for the latest 7.10 version :confused:

So if anyone has any advice on the best option to choose, and any guidelines or webpages that show me how to attempt this 2nd method, that would be very useful to me. Also when I do finally get Ubuntu installed (I hope), will I be given an option to choose which OS I want to run?

Thanks.

---

### Post by Pumalite on 2008-04-13
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Prepare your partitions. Then, install Ubuntu, go Manual and choose the partitions you already prepared.
Keep in mind that the is a limit of 4 primary partitions per HDD. You need to make an 'extended' partition, and within that you can make as many 'logicals' as you want. Windows needs a primary to boot, but Ubuntu is happy with logicals.

---

### Post by Ondas on 2008-04-13
thx, but I already have gparted on the ubuntu live cd install disc, so why should I have to use it independently? also how do you make an extanded partition and prepare the logical partitions for ubuntu?
Is there a guide that shows this procedure? I have no idea how many logical partitions are required? I was hoping to shrink my fat32 partition and let the install prgram set up the required partitions itself, but maybe this isn't possibele? Thanks.

---

### Post by Pumalite on 2008-04-13
Post:
sudo fdisk -lu

---

### Post by Ondas on 2008-04-13
ok, thanks.

---

### Post by Pumalite on 2008-04-13
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

