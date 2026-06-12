---
title: "Hard drive erased after trying to install Ubuntu 14.04"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by randolph.brisbon on 2014-06-20
Hi,
I tried installing Ubuntu 14.04 over a laptop that had Windows 7 Professional and this is what happened.

I pressed the option that says to erase windows and install Ubuntu onto it. I did and it came up with a message that said I couldn't install Ubuntu. I didn't have anything important on the laptop but now it can't load up Windows.

Whenever I load it up it just has a black screen with a small line in the most left part of it. I later tried installing another Windows 7 and it said my hard drive had no data available on it to install Windows 7.

Is there a way I can recover the data so I can install Ubuntu? 

Also what is the proper way of installing Ubuntu over a laptop with Windows?

My laptop model is hp presario cq56. I'm most likely thinking I can do nothing about it and will have to get another hard drive?

Thanks,
Randolph

---

### Post by yancek on 2014-06-20
> I tried installing Ubuntu 14.04 over a laptop that had Windows 7 Professional 

You mean you tried to install Ubuntu 14.04 on a laptop which also had windows 7 on it?

> I pressed the option that says to erase windows and install Ubuntu onto it. 

That means you will overwrite everything on the dirve from the master boot record to your windows system and data partitions.  Is that what you meant to do?

>  it came up with a message that said I couldn't install Ubuntu

The messages are usually not that cryptic.  Any specifics?

>  I later tried installing another Windows 7 and it said my hard drive had no data available on it to install Windows 7.


I don't understand that.  Why would it need any data on it.  windows is installed all the time to blank drives.  Are you sure about the message?  Do you have an actual windows installation medium, CD/DVD/USB?

I'm not sure what you mean by the 'proper way'.  If you want to boot both windows 7 and Ubuntu, I would suggest you read the tutorial below, carefully and thoroughly.  This is particularly important if you are unfamiliar with Ubuntu/Linux.  I noticed there are countless tutorials on installing Ubuntu but, almost all are the erase disk and install Ubuntu which is a windows type installation, overwrites everything.  Good luck and post back if you have any questions.   

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

You don't "need" another hard drive but sometimes, for new users in particular it is easier.

---

### Post by randolph.brisbon on 2014-06-20
> **yancek said:**
> You mean you tried to install Ubuntu 14.04 on a laptop which also had windows 7 on it?



That means you will overwrite everything on the dirve from the master boot record to your windows system and data partitions.  Is that what you meant to do?



The messages are usually not that cryptic.  Any specifics?



I don't understand that.  Why would it need any data on it.  windows is installed all the time to blank drives.  Are you sure about the message?  Do you have an actual windows installation medium, CD/DVD/USB?

I'm not sure what you mean by the 'proper way'.  If you want to boot both windows 7 and Ubuntu, I would suggest you read the tutorial below, carefully and thoroughly.  This is particularly important if you are unfamiliar with Ubuntu/Linux.  I noticed there are countless tutorials on installing Ubuntu but, almost all are the erase disk and install Ubuntu which is a windows type installation, overwrites everything.  Good luck and post back if you have any questions.   

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

You don't "need" another hard drive but sometimes, for new users in particular it is easier.

1st question - Yes just over a computer (meaning to install it over windows 7 and run) that had windows 7 on it.

2nd question - I just meant to install it over windows and work. After I did this I waited a few minutes (15 to 20) then it said it couldn't install Ubuntu. After this I tried installing another windows 7 iso from a dvd and it said within the install screen that my main (and also other hard  drive) didn't have any available data on it. 

3rd question - It said something about an error and then said it would report it to a developer. I'm not too sure about this and could try it again to confirm.

4th question - I don't want to install them side by side, but just Ubuntu over windows. But now it's saying that I don't have any hard drive space to install anything. Within the windows 7 iso menu after you click install on the second install option (I think it was something about a partition drive I forgot what it was) it says zero mb for both the main hard drive and the other (sub) hard drive.

I just need to know how to install Ubuntu onto the laptop and get back my hard drive space (if I can).

Thank you.

---

### Post by oldfred on 2014-06-21
If partition table was created with Ubuntu installer and used entire drive, then Windows will not see drive as it does not see Linux partitions. If you want to reinstall Windows you have to remove all partitions or create a primary NTFS formatted partition with the boot flag.
Or if you have a gpt partitioned drive, Windows will only install in UEFI mode. But if you boot installer in BIOS mode it then will not let you install.

Install process is the same even if you do not want dual boot.
       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

Are you using Something else to manually create partitions?
      
 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by randolph.brisbon on 2014-06-23
> **oldfred said:**
> If partition table was created with Ubuntu installer and used entire drive, then Windows will not see drive as it does not see Linux partitions. If you want to reinstall Windows you have to remove all partitions or create a primary NTFS formatted partition with the boot flag.
Or if you have a gpt partitioned drive, Windows will only install in UEFI mode. But if you boot installer in BIOS mode it then will not let you install.

Install process is the same even if you do not want dual boot.
       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

Are you using Something else to manually create partitions?
      
 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

I read some of them and don't understand what some of the terms mean. I just want to install Ubuntu over Windows 7 on the Hp presario cq56. Could you give me a guide just for that? Every time I try to install it it says that I don't have enough space. May you also give me a guide to get my space back?

---

### Post by SuperFreak on 2014-06-23
If you have a Ubuntu Live DVD/USB insert it and boot  to it. Choose TRY.Open GParted and try and get a screenshot showing partitions and post

---

### Post by Bucky Ball on 2014-06-23
*Thread moved to **Installation & Upgrades**.*

> **SuperFreak said:**
> If you have a Ubuntu Live DVD/USB insert it and boot  to it. Choose TRY. Open GParted and ...

... then delete all partitions on the drive, close Gparted, click the 'Install' icon, choose 'Something Else' when you get to the partitioning section of the install and partition manually something like this:

/ = where the OS goes, about 20Gb okay;
/home = where your personal data and settings go, large as you like;
/swap = 2Gb fine, at end of drive after /home. 

Done. Get back to us with any problems you encounter along the way.

---

### Post by randolph.brisbon on 2014-06-28
> **SuperFreak said:**
> If you have a Ubuntu Live DVD/USB insert it and boot  to it. Choose TRY.Open GParted and try and get a screenshot showing partitions and post

I'm up to the point you talked about, but I can't do anything because my left clicker on my mouse won't work. The portable clicker is out of operation. 

Is there a way I can get the left clicker to work?

---

### Post by randolph.brisbon on 2014-06-28
Tried installing Windows 7 and ended getting it to work (I'm kinda addicted to Ubuntu more than Windows) and wanted to install Ubuntu instead. Guess it wasn't meant to be. 

I have another laptop I just need to uninstall windows 7 with and might be able to put Ubuntu onto (it's the same model as the current one).


Thank you for the help.

---

### Post by Bucky Ball on 2014-06-28
Good news. Please mark the thread as solved to help others. Thanks.

---

