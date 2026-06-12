---
title: "Installing ubuntu on usb"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by coolgmlvish on 2011-06-13
I have a transcend pendrive USB of 16 GB . I installed Linux ubuntu and i am able to allot only 4gb for working with linux ubuntu. I want to utilize my maximum space of 16gb USB. 
Can i alot more disk space for Linux in my USb ?
please provide me the method to do that ?

Thanks,

---

### Post by sanderj on 2011-06-13
> **coolgmlvish said:**
> I have a transcend pendrive USB of 16 GB . I installed Linux ubuntu and i am able to allot only 4gb for working with linux ubuntu. I want to utilize my maximum space of 16gb USB. 
Can i alot more disk space for Linux in my USb ?
please provide me the method to do that ?

Thanks,

It seems to be possible (first hit on a Google search): [http://goo.gl/QiYzC](http://goo.gl/QiYzC)

HTH

---

### Post by haze_skw on 2011-06-13
I have USB 8 GB, for ubuntu 11.04 installation, with 2 partition 1st 111 MB for swap and 2nd all the rest with ext4 for /, and now I run from USB with Ubuntu 11.04.

I am sorry my english poor

---

### Post by Joe of loath on 2011-06-13
> **haze_skw said:**
> I have USB 8 GB, for ubuntu 11.04 installation, with 2 partition 1st 111 MB for swap and 2nd all the rest with ext4 for /, and now I run from USB with Ubuntu 11.04.

I am sorry my english poor

Don't bother with swap on a USB stick, it's too slow to make any difference, and there's a small chance you could wear out the flash memory with all the R/W cycles.

---

### Post by coolgmlvish on 2011-06-13
> **sanderj said:**
> It seems to be possible (first hit on a Google search): [http://goo.gl/QiYzC](http://goo.gl/QiYzC)

HTH

I am unable to follow the instructions in the above site .... By any means my casper parttion doesnot exceed more than 4gb . I want to utilize the maximum of my disk space in Linux

---

### Post by Joe of loath on 2011-06-13
Have you read them fully? 

> To make the persistence larger (> 4GB), while still on your normal Ubuntu Installation, mount the pendrive if it is not mounted already. View the files in the FAT32 partition of the pendrive. You will now be able to see a file called casper-rw. It will be the same size as the value set on the slider. Delete this file. Open gparted :

gksudo gparted

select the live usb. There will be a single partition only. Resize it so that you can have two partitions. You only need the current partition to be as large as it is already. You can safely move the resizing slider all the way to the left until there is just enough breathing space between the slider and the end of the first partition (coloured block). Make the newly created free space an ext4 or ext3 or ext2 partition and label it "casper-rw" without the double quotes. Hit apply changes. So now you have two partitions, the fat32 partition and the ext4 partition called casper-rw. This partition can be of any size and will be responsible for saving your data between boots. You can now boot using the usb drive and any changes you make will remain. 

---

