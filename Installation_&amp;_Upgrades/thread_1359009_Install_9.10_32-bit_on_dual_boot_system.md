---
title: "Install 9.10 32-bit on dual boot system"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by domfaid on 2009-12-19
Hi,

I tried last night to install a 32--bit Ubuntu 9.10 on top of a system (ThinkPad T61) that has a dual boot of Win XP SP3 and Ubuntu **64-bit** 9.10. 

Now the strange thing is that Gparted does not recognize the partitions on the systems (there are 2 NTFS partitions for Win and 2 for Ubuntu - one swap and one /).

Can somebody help me fixing this? I want to downgrade from 64-bit to 32-bit because of incompabilities/complications in software that prevents me to use Ubuntu in my day-to-day job (Cisco VPN, VMWare, Oracle 10g XE, WebLogic Workshop...).

Thanks a lot.
PS/ I have done an upgrade from 9.04 64-bit to 9.10 64 beta and then to the GA without any hassle (well actually one little thing: my win partitions requires authorizations for access while before it did not).

Dom

---

### Post by phillw on 2009-12-19
> **domfaid said:**
> Hi,

I tried last night to install a 32--bit Ubuntu 9.10 on top of a system (ThinkPad T61) that has a dual boot of Win XP SP3 and Ubuntu **64-bit** 9.10. 

Now the strange thing is that Gparted does not recognize the partitions on the systems (there are 2 NTFS partitions for Win and 2 for Ubuntu - one swap and one /).

Can somebody help me fixing this? I want to downgrade from 64-bit to 32-bit because of incompabilities/complications in software that prevents me to use Ubuntu in my day-to-day job (Cisco VPN, VMWare, Oracle 10g XE, WebLogic Workshop...).

Thanks a lot.
PS/ I have done an upgrade from 9.04 64-bit to 9.10 64 beta and then to the GA without any hassle (well actually one little thing: my win partitions requires authorizations for access while before it did not).

Dom

Are you booting off a Gparted CD ? - Mounted file systems cannot be altered. By using the LiveCD version of Gparted it should see all your partitions. It's available from here -->  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You'll be wanting the latest stable release which is here --> [http://sourceforge.net/projects/gparted/files/gparted-live-stable/OldFiles/0.4.6-1/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/OldFiles/0.4.6-1/)

Regards,

Phill.

---

### Post by domfaid on 2009-12-19
Hi Phill,

I mentioned GParted because I think that is what is used under Ubuntu for partitioning a new system. Using the 9.10 i386 Live CD, I tried to install but on the partitioning screen, he showed my drive as blank (no partitions at all). So I exited the install and came in the live environment of Ubuntu and there I started GParted (from Admin menu) and I got the same result (meaning: zip, nothing).

As I am now writing form the current Ubuntu installed on that machine (9.10 64-bit) I just know what goes wrong. 

I have downloaded a 9.04 i386 install cd and will see if with that one I can see my partitions. If not, I will have to do some thinking because it means something is screwed badly on my system (though so far, Windows and Linux are working fine).

Thanks for any insights.
Dom

---

### Post by bzhao on 2009-12-19
> **domfaid said:**
> Hi,

I tried last night to install a 32--bit Ubuntu 9.10 on top of a system (ThinkPad T61) that has a dual boot of Win XP SP3 and Ubuntu **64-bit** 9.10. 

Now the strange thing is that Parted does not recognize the partitions on the systems (there are 2 NTFS partitions for Win and 2 for Ubuntu - one swap and one /).

Can somebody help me fixing this? I want to downgrade from 64-bit to 32-bit because of incompabilities/complications in software that prevents me to use Ubuntu in my day-to-day job (Cisco VPN, VMWare, Oracle 10g XE, WebLogic Workshop...).

Thanks a lot.
PS/ I have done an upgrade from 9.04 64-bit to 9.10 64 beta and then to the GA without any hassle (well actually one little thing: my win partitions requires authorizations for access while before it did not).

Dom



The reason is that parted require partition table must be very very standard one. I did met this issue before. I did fix it by fdisk manually. 

Can you paste the result of "fdisk -l /dev/sdx"
and Tell me which partition is missing with in parted


Bill Z

---

### Post by domfaid on 2009-12-19
Hi Bill,

I am not sure what the issue is. Here is the output of your cmd:

[FONT=Courier New]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa090a090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5838    46886912    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5838        6360     4195328    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            6360       14593    66133512+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            6360       11590    42009552    7  HPFS/NTFS
/dev/sda6           14469       14593     1003999+  82  Linux swap / Solaris
/dev/sda7           11591       14468    23117503+  83  Linux

Partition table entries are not in disk order[/FONT]

The funny thing is all my partitions are visible. However in the install, it showed none!

Thanks
Dom

Current system is Linux dfaidherix 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

---

### Post by bzhao on 2009-12-19
> **domfaid said:**
> Hi Bill,

I am not sure what the issue is. Here is the output of your cmd:

[FONT=Courier New]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa090a090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5838    46886912    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5838        6360     4195328    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            6360       14593    66133512+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            6360       11590    42009552    7  HPFS/NTFS
/dev/sda6           14469       14593     1003999+  82  Linux swap / Solaris
/dev/sda7           11591       14468    23117503+  83  Linux

Partition table entries are not in disk order[/FONT]

The funny thing is all my partitions are visible. However in the install, it showed none!

Thanks
Dom

Current system is Linux dfaidherix 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Dom,

You case is not the same as me. I don't have "Partition 1 does not end on cylinder boundary" issue. That mean you have used windows or other tool to create partition, while I alway use linux to create partitons. 

I still can advise you to try the below method:
1. back up partition table first and make sure you can go back.
2. sudo fdisk /dev/sdx
3. press x to enter into advance page
4. press f to fix partition order.
5. press w to write partition table and exit.

Try again!
This is not a resolution but I feel it help.

PS: fdisk is very low level tool for disk partition. it can fix/show partions strongly. it also can kill your disk.

---

### Post by domfaid on 2009-12-19
I have tried to fix the partitions under windows using part magic but no chance.

How can I do a partition table backup? I have never played so far with parted or fdisk to change the partition table directly. A few tips and instructions would be welcome (it would be bad if I screw my work system and got never Linux nor Windows working...)

Thanks in advance.
Dom

---

### Post by bzhao on 2009-12-19
> **domfaid said:**
> I have tried to fix the partitions under windows using part magic but no chance.

How can I do a partition table backup? I have never played so far with parted or fdisk to change the partition table directly. A few tips and instructions would be welcome (it would be bad if I screw my work system and got never Linux nor Windows working...)

Thanks in advance.
Dom

Partition table backup method:
under window:
 run regedit command: you can find out item within pulldown menu to do that(backup and restore). 

under linux:
#####################
###Read firtly note: Please make sure that below command is correctly typed by you not by pasting because the error will kill you disk
######################
backup:
&#12288;sudo dd of=/root/mbr if=/dev/sda bs=512 count=1
####backup the first sector of disk
restore:
&#12288;sudo dd if=/root/mbr of=/dev/sda bs=1 skip=446 count=66
####bs=1 skip=446 count=66"  the partition tale data is the loation in the backuped mbr file
&#12288;

---

### Post by raymondh on 2009-12-19
> **domfaid said:**
> Hi Phill,

I mentioned GParted because I think that is what is used under Ubuntu for partitioning a new system. Using the 9.10 i386 Live CD, I tried to install but on the partitioning screen, he showed my drive as blank (no partitions at all). So I exited the install and came in the live environment of Ubuntu and there I started GParted (from Admin menu) and I got the same result (meaning: zip, nothing).


try this

Boot into the liveCD of 9.10 and in live session, access a terminal ..

```
sudo apt-get remove dmraid
```

Exit terminal and click install ... see if it recognizes the partitions.

Regards,

---

### Post by domfaid on 2009-12-20
Raymond,

I tried it but it did not fix my issue. Still no partitions recognized. Thx for the suggestion.

Bill,

I still toying with the ideas to leave my system as is, or maybe to perform a full reinstall (Win and Ubuntu). I am not sure I want to push my luck with playing with the partition table.

Thanks for the great help and suggestions! 
Dominique

---

