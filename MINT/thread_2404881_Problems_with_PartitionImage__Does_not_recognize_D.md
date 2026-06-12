---
title: "Problems with PartitionImage / Does not recognize Drives / Partitions"
date: 2018-10-29
forum: MINT
---

### Post by 2heinzi2 on 2018-10-29
Hello Ubuntu-folks,

though me being a user of Linux-Mint (Version 18.1 64bit Mate), possibly one of you guys around might be capable of helping with 2 questions, as Linux Mint is known as a derivative of Ubuntu. As a Flash-drive-based live-version running without any problems on my System up to now (2-core 64 bit Lenovo Thinkpad [8 GB Mem]), I nonetheless face some difficulties using Partition Image in order to create compressed drive / partition images, dd or its graphical "counterparts" only being capable of generating raw-images.

Question 1: The problem is - while having never occurred up to now, and still concerning only PartitionImage - that PartImage does not properly recognize my drives and partitions. Instead of  showing an appropriate list, there only shines up a strange column of entries "ram1" - "ram7", each of them with a capacity of 64 MB (cf. attachment).


Question 2: Another question of minor importance is whether there could be a possibility (as is the case at least concerning gentoo-based System Rescue CD) of creating an appropriate  entry for Partition Image within the system's menu structure. Tips like the following [https://www.linuxquestions.org/questions/linux-software-2/linux-mint-installed-clonezilla-but-where-is-it-4175577072/](https://www.linuxquestions.org/questions/linux-software-2/linux-mint-installed-clonezilla-but-where-is-it-4175577072/) didn't work.

The people in the original Mint forum (the german one, the english appearing quite abandoned) virtually came around  with nearly dozens of answers and tips - but, sadly, none of them with respect to the questions originally asked.

Has anyone around here got an idea, especially concerning question 1, of how to cure this or what the reasons may be? 

Thanks & best regards

Heinzi

---

### Post by oldfred on 2018-10-29
Moved to Mint sub-forum.

Many of the tools to create live boot image, do not create a partitioned image, but use the hybrid DVD/flash  drive configuration. That has no partitions. 
To use flash drive you have to convert it back to partitions:
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

