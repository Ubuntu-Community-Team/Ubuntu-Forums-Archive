---
title: "Partitioning confusion: Want to install Ubunto onto a XP native laptop."
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by regbsn on 2008-02-15
I have a Satellite 1115 w/20G HD and 9.6G freespace as per "properties" tab for HD from inside XP. I need to keep XP as a test platform for my other PC, but have been dying to have a Linux platform to learn from and operate as my primary platform. The partitioning program off the Live CD suggests 12.9G partition. no matter what I slide the scale to I get a partitioning error message. I am then taken to a :"prepare partitions" screen with the following values:

     DEVICE        TYPE   MOUNT POINT   FORMAT?       SIZE         USED   
     /dev/sda1    ntfs      /media/sda1                       20003 MB      0 MB

     "format?" just has a check box. It says that I need to specify a 
      partition for the root file system (mount point "/") with a minimum 
      size of 2 GB and a swap partition of at least 256 MB. You may also
      set up other partitions if you wish.

Please help. I am affraid of making the XP partition unusable. I also have no idea of what it is asking me to do or how to do it.

Thanks,
Reese

---

### Post by themusicwave on 2008-02-15
When I installed Ubuntu I simply had it shrink my windows partition.

You do need to be careful, selecting the wrong this WILL erase your hard drive.  

Basically you want to have Ubuntu shrink your Windows partition.  You want to have it make 2 partitions one for the root directory which is / and one for swap.

Most people say the swap partition should be 2 times the size of your RAM, so if you have 1GB ram get 2 GB swap.

You do not want to format your Windows partition, just shrink it.  Then format the root partition as ext3 and the swap partition as swap.

Take your time and read carefully, it's not that bad.

Good luck,

Jon

---

### Post by oilchangeguy on 2008-02-15
> **themusicwave said:**
> When I installed Ubuntu I simply had it shrink my windows partition.

You do need to be careful, selecting the wrong this WILL erase your hard drive.  

Basically you want to have Ubuntu shrink your Windows partition.  You want to have it make 2 partitions one for the root directory which is / and one for swap.

Most people say the swap partition should be 2 times the size of your RAM, so if you have 1GB ram get 2 GB swap.

You do not want to format your Windows partition, just shrink it.  Then format the root partition as ext3 and the swap partition as swap.

Take your time and read carefully, it's not that bad.

Good luck,

Jon

the user is getting short on hard drive space, and doubling your ram is never needed. simply let ubuntu decide what it needs during the install. do you manually adjust windows page file (swap)?

---

### Post by regbsn on 2008-02-20
OKay....update.

Reduced RESTORE POINT memory allocation to only 400Mb, was using over 2800Mb. I couldn't understand why every time i deleted stuff, my freespace decreased. Swap file also reduced to 512 Mb as equal to my memory (upgraded from 256 Mb). I now have 10.9 MbMy problem is that the partitioning program bundled with Ububtu 7.10 still wants to use 12.9 Mb.
I am awaiting VCOM's System Commander 7.0 to remove a few essential windows only programs to put on an external drive so that I can free up even more space.

On a side note, I read that i could install a mutually usable partition in Fat32 format so that I could share files for read/write use. So if so, how large does the root directory need to be for Ubuntu. I do plan on adding extensions, new desktop managers for eval, games, ect. Should I place them on the root or another partition. I have read various posts and am more confused than ever!

PLease help,
Reese

---

