---
title: "Installing 10.04 across two hdds"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by skimm on 2010-04-09
Hey all,
First post which I am pretty sure will have a simple answer.  I have a 32 GB SSD that I use as my Windows 7(64bit) install drive.  It has about 9gb free at this point in time and I would like to install the 10.04 beta onto the SSD as well.  I made one attempt prior to this and put the root partition and the swap on the SSD and the ext3fs on my other 640gb HDD.  It seemed to install fine, but GRUB was not working properly and I had to remove the Ubuntu install and use Windows system restore to get things working properly again.  I was just wondering what the best way is, if possible to install Ubuntu to the SSD and use the standard HDD as storage for applications and media.  I have moderate experience with linux, and a terminal and any help would be greatly appreciated.  Thanks.

Also, it is the 64bit version of 10.04, and my hardware specs are:

3.8GHz AMD Phenom II X4
4GB DDR3

---

### Post by oldfred on 2010-04-09
The beta of 10.04 is still having soem issues. There is a entire sub-forum for Lucid.

I installed the first beta and had issues but finally got it to work. I boot from sdc and fortunately for me grub installed to sda. There is an advanced button on the screen where you finalize partitions. The advance button lets you choose where to install grub. If you do not use your other drive's MBR I would install grub there even though it is best to have grub on the same drive as the Ubuntu install. 

I am not sure what you meant by ext3fs as that is the driver for windows to read ext3 partitions. Since you only have 9GB you need to have /home on your data drive. I have seen several posts or blogs on SDD and settings to improve performance. With 4GB of memory you should not normally be using swap so having it on the other drive would be ok. If you keep swap on you SSD your root partition may be too small and swap would probably not be used unless you did video editing or loaded every program at once.

---

### Post by lvleph on 2010-04-09
It looks like you might want / mounted on the SSD and /home,/bin,/usr mounted on partitions (extended partition would probably be best) on the HDD. This makes the required space on the SSD relatively small. Unfortunately this also may make programs run slower as the kernel will run them from a seperate slower hard drive. It is also possible that you may not even notice.

---

