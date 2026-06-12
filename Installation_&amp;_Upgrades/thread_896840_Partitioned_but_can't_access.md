---
title: "Partitioned but can't access"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by SilverHawk10 on 2008-08-21
I partitioned my hard drive to contain Ubuntu and Windows Vista.  However, I do not have an option to access the Ubuntu partition.  I turn on my computer and it automatically boots the Windows Vista.  How do I get a screen after I boot to ask me to either load the Ubuntu or Windows?

---

### Post by lordadi on 2008-08-21
If this is a fresh install (of Ubuntu), then put in the Ubuntu live cd and reinstall, it should fix your problems. It sounds like grub was'nt (for some reason) installed when you installed Ubuntu.

---

### Post by SilverHawk10 on 2008-08-21
But if I reinstall, in step 4 it wants me to repartition my hard drive and i dont want to lose even more space.  I'm trying to access that memory that it is already installed on.  I have a program that allows me to view my Ubuntu info from Vista, can i just add the Grub File or something?

---

### Post by lordadi on 2008-08-21
No, it has to be installed to your disk i.e. it has to know what systems etc there are. Also, you can just rewrite over the old Ubuntu partition. In the partition editor, find and select the partition that registers as an ext3 partition. Tell it to use that partition to install Ubuntu.

---

### Post by SilverHawk10 on 2008-08-21
On step 4 i click manual, and I see the ext 3 partition u are referring too.  However, I select it or like edit it and it says something about no Root. I tried to edit the partition to be Fat32, but that also gave the same thing.  Theres another drop down box with the options DOS and Windows....and I didnt click either....should I click one of those?

---

### Post by lordadi on 2008-08-21
Isn't there something that says guided: use partition XYZ or hda (X,Y)?

---

### Post by SilverHawk10 on 2008-08-21
i'll check again, but i dont believe i have that...I have 3 options 1) guided and like resizes and everything, 2) guided and do entire hard drive 3) manual

---

### Post by SilverHawk10 on 2008-08-21
and the error is like root system not defined or something

---

### Post by lordadi on 2008-08-21
Isn't there something under manual that says use largest contiguous disk space? If not, then choose to resize the disk and install Ubuntu on a tiny-ish part. After the install, use the GParted live CD to delete the old install's partition (the extended partition) and resize the tiny new one's extended partition to take up the freed space. Unfortunately, I do not see an easier way out.

---

### Post by DavidTangye on 2008-08-21
> **SilverHawk10 said:**
> and the error is like root system not defined or somethingThat is correct. It is saying that you have not indicated which partition is to be the root partition.

In the Manual Partitioning option, select the partition that you used before to install Ubuntu onto again. Select the partition, and hit enter to adjust its details. On the list of about 8 options that appear, near the top, you need to have it set to Use it, and next down to Use it for / (ie as the root partiton), and next down to format it as ext3, then select the option near the bottom of the list that is something like 'Finished defining this partition'. (I hope that is right, I am working off memory, and cannot find any screenshots of the procedure anywhere.) You can inspect all your partitions this way, then select to write the new partition table based on what you have done. Make sure it is only going to reformat the partitions you want done, before you hit the confirm option. The swap partition will be automatically selected to be reformatted, which is ok.

---

