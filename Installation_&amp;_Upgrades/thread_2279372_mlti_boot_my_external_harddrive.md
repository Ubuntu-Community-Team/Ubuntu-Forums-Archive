---
title: "mlti boot my external harddrive"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by ashiwnmanoj on 2015-05-23
hi all ,
      I am a windows 7 user and i want to learn ubuntu and so i decided to partition my 500GB pendrive into a 10GB and 490GB partitions. Now i have an ISO file of ubuntu in my system. when i tried to mount  the ISO file to the external drive 2 of 10GB using ultraISO software it detects both the partitions together [H:,I:,500GB] and asks me to format my entire hard disk which i never want to do. So i will be thankful if anyone could find me a way to solve this problem. 

thanking you

---

### Post by sudodus on 2015-05-23
Welcome to the Ubuntu Forums :-)

The easiest way to learn Ubuntu is to [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

And ***I think it would be easier if you have a small and cheap and reliable USB pendrive for testing and learning***. Dedicate it to the learning process. After that you will be able to use your 500GB pendrive with several partitions, where one partition can be accessed by Windows, and the other partitions are linux partitions.

See these links for more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL] particularly post #6 and #7.

---

### Post by ashiwnmanoj on 2015-05-23
Thank you so much for your response but the problem is I dont have a pendrive and I have only a harddisk. I just want to know if there s any possibility where I can have a partition with all my data and create another dedicated for linux (a boot-able partition) without affecting the data in other partition.

---

### Post by sudodus on 2015-05-23
I see. You wrote pendrive in the opening post, but meant harddisk. No worries, it happens to me too, that I think one thing and write another thing :-)

It is possible to use a hard disk drive in the same way as a pendrive. Do you mean that you have only one hard disk drive, or that you have one internal drive and one external drive, and both of them are hard disk drives?

Anyway, in both cases it is possible to make a dual boot system with Windows and Ubuntu. With two drives it is easier, you can leave the drive with Windows untouched, if you disconnect it (remove it) from the computer.

But I suggest to use another drive, either a DVD disk or a USB pendrive, and burn or flash/copy/clone the content of the downloaded iso file to it in order to have an install drive. There are other methods, for example to boot via grub from the iso file, but they are more complicated. It is possible but I would not use an external USB hard disk drive with a lot of valuable data as a USB boot drive, particularly not while still learning the basics about Ubuntu.

A small and reliable USB pendrive is cheap (for example Sandisk Cruzer Blade 4GB costs less than $ 10 ~ 10 &#8364; in many countries).

-o-

Before you continue, I have a couple of questions.

1. Have you got a good backup of all your personal data (documents, pictures, video clips ...)?

2. Is Windows installed in UEFI mode or BIOS mode?

---

### Post by ashiwnmanoj on 2015-05-23
oops i just noticed my mistake..I have an external hard disk partitioned.. and my window is in BIOS mode..but ur suggestion of taking a new usb pendrive sounds good and save so I will definitely follow that..but still my curiosity wants me to get the solution..I think i dont communicate my problem clearly.. ok i ll put it in this way.. i have an partitioned external harddisk in which one partition has data and the other is completely empty. When i try to mount my ISO ubuntu file into the free partition using a software I have installed on my windows7 computer it asks me to format both the partitions of my external harddisk..Y is it so? Am sorry if am exaggerating or my question is too silly to answer .. I will be greatful to you if u help me learn.. :) thank you

---

### Post by sudodus on 2015-05-23
> **ashiwnmanoj said:**
> oops i just noticed my mistake..I have an external hard disk partitioned.. and my window is in BIOS mode..but ur suggestion of taking a new usb pendrive sounds good and save so I will definitely follow that

:-)
> 
..but still my curiosity wants me to get the solution..I think i dont communicate my problem clearly.. ok i ll put it in this way.. i have an partitioned external harddisk in which one partition has data and the other is completely empty. When i try to mount my ISO ubuntu file into the free partition using a software I have installed on my windows7 computer it asks me to format both the partitions of my external harddisk..Y is it so? Am sorry if am exaggerating or my question is too silly to answer .. I will be greatful to you if u help me learn.. :) thank you

If the first partition in your external drive is a FAT32 partition it can be seen by Windows, and you can download and install ***Unetbootin for Windows*** and use it to install Ubuntu from the iso file to that FAT32 partition and that way make it a USB boot drive. But I think Windows cannot see the second partition (at least Windows used to see only one [and I think the first] partition in USB drives). If you turn it around, and the first partition is the big one, I guess you have the NTFS file system in that partition and it will be seen by Windows, but then Windows will not see the second partition, and it will be hard for Unetbootin in Windows to install Ubuntu into it, when it is not seen by the operating system.

---

### Post by ashiwnmanoj on 2015-05-23
thank you so much :) i understand :)

---

