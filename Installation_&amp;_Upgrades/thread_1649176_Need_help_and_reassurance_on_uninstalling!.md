---
title: "Need help and reassurance on uninstalling!"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by iamgrape on 2010-12-19
I'm going to delete the Ubuntu (9.04) volumes and leave only the Windows Vista volumes. Keep in mind that I am no expert here. Tell me if I am right. I was going to go into disk management in Vista and delete the Ubuntu volumes. Yes, no? Am I completely off and about to blow up my computer? Which volumes here should I delete? Here is a screenshot of my disk management window for reference:

[http://i1226.photobucket.com/albums/ee409/limerlima/paptitions.jpg](http://i1226.photobucket.com/albums/ee409/limerlima/paptitions.jpg)

Ahhhhh installing was no issue, but uninstalling is stressful!

---

### Post by PhantmKllr on 2010-12-19
I don't recommend uninstalling. In my experience, uninstalling Ubuntu never goes well, and ends up with a broken computer. The only safe solution is to wiping your hard drive and starting over...

---

### Post by lmarmisa on 2010-12-19
Welcome to the forums.

I believe you have a dual boot system Vista + Ubuntu 9.04. 

Therefore, I suppose you loader program is GRUB. If you delete the Ubuntu partitions, you will lose your GRUB loader too and your system will be unable to boot.

So, do not delete the Ubuntu partitions until restoring the Vista loader program!!!.

I do not know if you wish to get rid of Ubuntu or install a new version.

---

### Post by iamgrape on 2010-12-19
> **lmarmisa said:**
> Welcome to the forums.

I believe you have a dual boot system Vista + Ubuntu 9.04. 

Therefore, I suppose you loader program is GRUB. If you delete the Ubuntu partitions, you will lose your GRUB loader too and your system will be unable to boot.

So, do not delete the Ubuntu partitions until restoring the Vista loader program!!!.

I do not know if you wish to get rid of Ubuntu or install a new version.

I was between keeping Ubuntu and updating to the new 10.10 or just deleting it altogether. I am using GRUB, I forgot to mention that. Since you say deleting it usually yields bad results, do you say updating is easier?

---

### Post by lmarmisa on 2010-12-19
> **iamgrape said:**
> I was between keeping Ubuntu and updating to the new 10.10 or just deleting it altogether. I am using GRUB, I forgot to mention that. Since you say deleting it usually yields bad results, do you say updating is easier?

Yes, a fresh install of Ubuntu 10.10 re-using the partitions of 9.04 is the easiest solution, IMHO.

You will need to select manual selection of partitions during the installation procedure. Not difficult at all, but you should be sure about the steps to follow before you start the procedure.

---

### Post by iamgrape on 2010-12-19
Steps to follow?

---

### Post by lmarmisa on 2010-12-19
> **iamgrape said:**
> Steps to follow?

Please, post the output of this command:

```

sudo fdisk -l

```and I will send you the procedure for a new fresh Ubuntu 10.10 installation.

---

### Post by iamgrape on 2010-12-19
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78091a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1918       38875   296857620    7  HPFS/NTFS
/dev/sda4           38876       60801   176120595    5  Extended
/dev/sda5           38876       59906   168931476   83  Linux
/dev/sda6           59907       60801     7189056   82  Linux swap / Solaris

Thank you kind sir!

---

### Post by lmarmisa on 2010-12-19
> **iamgrape said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78091a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1918       38875   296857620    7  HPFS/NTFS
/dev/sda4           38876       60801   176120595    5  Extended
/dev/sda5           38876       59906   168931476   83  Linux
/dev/sda6           59907       60801     7189056   82  Linux swap / Solaris

Thank you kind sir!

You will need an Ubuntu 10.10 Desktop edition Live CD (64 bits if you wish) for the installation.

Boot your system into the Live CD and start the installation.

Image 1: no comment

Image 2: I recommend to tick "Install this third-party software"

Image 3: VERY IMPORTANT Select "Specify partitions manually (advanced)" 

I continue in the next post.

---

### Post by lmarmisa on 2010-12-19
Image 4: click twice on **/dev/sda5** partition

Image 5: Do not modify the "New partition size" (the size of my partition is different than yours, of course). Select "Use as: Ext4". Tick "Format the partition". Select "Mount point: /". Finally OK.

Image 6: Click on Install now and continue with the installation normally.

I hope you will have no problems with your installation.

Best regards,

Luis

---

### Post by Quackers on 2010-12-20
Also, if you boot into Vista and go to control panel and then Backup and Restore Centre you will see on the left side an option to "create recovery disc". If you have not made that cd yet do so. It is the Windows repair cd (not recovery discs) that you will need to repair your master boot record one day! :-) It's well worth doing!

Then if, one day, you want to leave just vista on there you can do so, by repairing the mbr that grub is using at present.

---

