---
title: "How can I losslessly create a dual boot Lubuntu and Ubuntu Studio?"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2015-05-10
Hello,

So I am running Lubuntu on one partition of my hard drive.  The other partition is empty.  I have the swap space assigned to it's own partition also.  
My question is this:  If I run the Ubuntu Studio installer, will it erase my Lubuntu partition?  or is there an option to install into it's own partition?
And also, after installation, will there be a boot menu so I can choose between Lubuntu (old) and Ubuntu Studio (new)?  

Please let me know. Thanks

---

### Post by Bashing-om on 2015-05-10
yoshi2; Hi !

yep:
> 
or is there an option to install into it's own partition

That option is "something else" , and in the installer point it to install onto the desired partition .
run terminal commands:
```

sudo fdisk -lu
sudo blkid

```
to be absolutely sure of where to install to .

[INDENT][INDENT]dual booting
[INDENT][INDENT][INDENT]cheap insurance
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-05-10
So, you have three partitions? One for Lubuntu, one empty and one for swap.

The Something Else option will run a partitioner that will list all the partitions. Select the partition you want Ubuntu Studio to go into and click Change.

In the dialog box in the Use As panel select Ext4 from the drop down menu. You can tick the Format box because you have not selected the partition with Lubuntu on. Make sure that to do not select the wrong partition. In the Mount Point panel select / as the mount point. Now click OK and you will be returned to the partition section.

You do not need to select a partition for swap as you already have a swap partition and the installer will make use of the existing swap partition. After double checking that everything is as it should be click Install Now.

As part of the install process the Grub boot loader will be installed into sda by default and as part of that process there will be a check for other operating systems and Lubuntu will be detected.

The first option in the new boot menu will be Ubuntu Studio with another option for Lubuntu. If you want Lubuntu at the top of the menu, let us know and we will tell you how to do it.

Regards.

---

### Post by yoshii on 2015-05-10
> **grahammechanical said:**
> So, you have three partitions? One for Lubuntu, one empty and one for swap.

The Something Else option will run a partitioner that will list all the partitions. Select the partition you want Ubuntu Studio to go into and click Change.

In the dialog box in the Use As panel select Ext4 from the drop down menu. You can tick the Format box because you have not selected the partition with Lubuntu on. Make sure that to do not select the wrong partition. In the Mount Point panel select / as the mount point. Now click OK and you will be returned to the partition section.

You do not need to select a partition for swap as you already have a swap partition and the installer will make use of the existing swap partition. After double checking that everything is as it should be click Install Now.

As part of the install process the Grub boot loader will be installed into sda by default and as part of that process there will be a check for other operating systems and Lubuntu will be detected.

The first option in the new boot menu will be Ubuntu Studio with another option for Lubuntu. If you want Lubuntu at the top of the menu, let us know and we will tell you how to do it.

Regards.


Hey thanks very much.  I think you've answered my questions.  Thanks

---

### Post by Bucky Ball on 2015-05-11
PS: Using 'Something Else', your UStudio install can use the existing /swap. You DON'T need two. Same if you have a /home partition already. Just mark them to 'Use' but NOT to 'Format'. The system will consider these as your /swap and /home partitions and install accordingly. Good luck and don't hesitate to pipe up if you get in a pickle.

---

