---
title: "Dual Boot: Need more HD spaces after install Ubuntu"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by candyoff on 2006-10-27
Hi

I have installed my Ubuntu few months ago (dual boot with windows)
These days I have almost used up all the hard disk space. 
Can I know how can I allocate more spaces to this linux partition. 
Is it I have to defrag my windows partition first, then allocate the spaces from there. Will this corrupt my system (both ubuntu and windows)

Regards

---

### Post by Beaucephus on 2006-10-27
If you have extra space on your windows drive you can resize your drives with a program called qtparted.  

You can also just mount the windows partition and create a folder for saving files. 

I set up my hard drive to have 4 partitions like this

1 - Windows  / NTFS
2 - File Space / FAT32
3 - Ubuntu / (Ext3)
4 - Linux Swap  

I use the FAT32 partition for storing files I will use in windows and linux like pictures and such.

Read up on qtparted and back up your data before attempting ANY partition reconfiguration.

---

