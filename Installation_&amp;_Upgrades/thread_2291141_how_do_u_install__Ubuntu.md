---
title: "how do u install  Ubuntu ?"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by acepro71 on 2015-08-18
ok so i am not able to dual boot this os 

installed windows 7 , 8 , 10 first ! then tried to install ubuntu 15 / 14 LTS ... it wont show the option to dual boot with windows 

having the same issue every time [IMG]http://linustechtips.com/main/public/style_emoticons/default/sad.png[/IMG] now i am currently on 8.1 damn  i still can not install it :.. please help 

my hard disk i checked everything i formatted my entire drive 3 times >.> [https://imgur.com/xRQaLSv](https://imgur.com/xRQaLSv)

the install screen > [http://imgur.com/wyZECIM](http://imgur.com/wyZECIM)  , [https://imgur.com/BRzUNmK](https://imgur.com/BRzUNmK)  , [https://imgur.com/Wa2vbHD](https://imgur.com/Wa2vbHD)


and if i go something else [https://imgur.com/C0WpiAa](https://imgur.com/C0WpiAa)  it shows whole 500 gb disk [IMG]http://linustechtips.com/main/public/style_emoticons/default/sad.png[/IMG] not the partiton i created for it separately which is un-partitioned ..


please help

---

### Post by ajgreeny on 2015-08-18
As you are already using Windows 7, 8, and 10 on the machine I imagine the system is partitioned with a GPT partition table and UEFI, and therefore you will need to boot the install medium (DVD or USB) in UEFI mode, and your ubuntu partitions will also need to be in GPT partitions and installed in UEFI mode.

To understand all this more fully, should you not know what I mean, have a good read through [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which may help you out, but if it is all still gobbledegook come back again.

To help us understand more fully it will be worth following the instructions at the link in my signature below for Boot-Repair and posting the pastebin link you are given.  Do not accept any default repair options; just run the boot-info script and we may then be able to help you out more.

---

### Post by grahammechanical on 2015-08-18
The first image shows that you have Primary partitions on that disk. This would indicate that the motherboard has a BIOS boot system and there is a 4 Primary partition limit on each hard disk with the BIOS boot system.

The installer is offering the only options it can. It cannot offer to install alongside because it needs to use a certain method to work around the 4 Primary partition limit. The work around is to create an Extended partition and in the Extended partition create 2 Logical partitions, one for Ubuntu and one for swap. But here is the catch - the installer cannot use the unallocated space because Extended partitions are a special kind of Primary partition and you have already reached the 4 Primary partition limit.

The Something Else option will not let you access to the partitions to prevent you from unintentionally deleting data that you do not want to delete. So, it shows you the whole disk to give you the choice of formatting the whole disk. It is the "all or nothing" option.

The simple truth is that you need to delete one of those primary partitions so that the installer can create an Extended partition and install Ubuntu into the extended partition.

Regards.

---

### Post by ajgreeny on 2015-08-18
Ah!  I could not see the details of the screenshots when I saw this earlier, but grahammechanical is correct; you are not using UEFI so you can forget my earlier comments.

Unfortunately where Windows is concerned I can not help with which partitions to remove, but it looks as if the data E: drive is totally empty so that would appear to be the one to delete and then use for installing Ubuntu using an extended partition in that space with the logical Ubuntu OS partitions inside that, but make sure that it really is empty first.  

You will need to leave the deleted partition as empty space rather than make a partition using Windows, and the Ubuntu installer will then find this and show it as unallocated space.

---

