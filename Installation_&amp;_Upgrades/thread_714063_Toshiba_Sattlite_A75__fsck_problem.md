---
title: "Toshiba Sattlite A75 : fsck problem"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by JackInBottle on 2008-03-03
Finally I installed U7.1 and brought up the system. I had some problems on the installation.
The major problem was the disk partition.
I had WinXP pre-installed  and use 8G free space for Ubuntu. The patition was used for a slackware linux and every thing was fine. Now I reinstall Ubuntu over these slackware linux. but problem comes.

The live CD worked fine and went through the installation (include format the filesytem). When reboot the system, it hanged with black screen. 

Okey, one more try. I delete the slackware disk partitions and use UBuntu to re-partition the disk, installed again, still hanged on black screen when reboot.

Reboot the machine on save recover mode, I found fsck report disk error and hanged there! But there should not be error, it is bug of fsck!

Press Ctrl+Alt+Del , the system exit the fsck, and booted into run level 1 console.
I typed in telinit 3 to bring the system into GNome gui and bingo every thing worked.
Reboot the machine and still hanging on fsck. GEE.
I use slackware boot disk boot the machine and use cfdisk delete the UBuntu partitions. 
Third time install the ubuntu. This time I use ubuntu's partition (the third or second option to partion the disk, not manually, but I do not remember exact one). and this time went through no more errors on fsck.

I feel that Ubuntu needs some special disk partition and those special setting can not be done by manually. There are very little docs to describe these special demands.

Three times installation and finally get Ubuntu running on my laptop. I still like Ubuntu when I first see it. 

Wireless works out of the box( need puchin the WEP key ofcause)

Sound card(didn't work on live CD, but works fine after install to harddrive, maybe it was fixed by updating)

Video card: support LiveCD's bootup framebuffer GUI, but after install to harddrive, The framebuffer  mode for booting is not supported anymore ( no booting GUI, juct black screen untill login screen pops up)

Software compatibility:
VIM works fine, but GVIM has a start problem on check the character_size function hence inside  GVIM all the keyboard keys are all messed up with wrong keys. 
Media Player doesn't support RealOne and there is no place to install the CODEC.

Interface: the original fonts for web browser and gui are ugly. I grab all the windows Font (from my XP partition's C:\Windows\Fonts\, into Ubunto's font fold, and immediately all these true type Win-Fonts works for ubuntu, without any other commands and configuration file modification. to enter the Ubuntu fonts fold, goto appearence and modify the font, there is a button to let you show the fonts fold which is a kind of sever address)

Except all these, I am still  happy with Ubuntu. It simplifier lots of the configurations.

Sorry for my poor English!

---

