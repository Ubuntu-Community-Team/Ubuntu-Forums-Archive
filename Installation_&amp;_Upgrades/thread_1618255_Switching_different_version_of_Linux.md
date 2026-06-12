---
title: "Switching different version of Linux"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by somuchdirt74 on 2010-11-10
I'm completely new to Linux, I have a dell inspirionB130 and I installed mandriva dual boot with windows 7.. However I was not able to connect to a wireless network, but yet I could when i switched back to windows 7. Ive also just been wanting to try other versions of Linux to see which one I would prefer.. But Im not really sure on how to uninstall Linux or replace it with different version.. I have read in this link [Mandriva Installed with Windows; Looking to try another Linux Distribution  Read more: http://www.brighth*******/computing/linux/articles/35620.aspx#ixzz14tjZ2Hgv]("http://ubuntuforums.org/Mandriva%20Installed%20with%20Windows;%20Looking%20to%20try%20another%20Linux%20Distribution%20%20Read%20more:%20http://www.brighth*******/computing/linux/articles/35620.aspx#ixzz14tjZ2Hgv") here and I was wondering if this was a correct way of doing it, I just didnt know if some kind of conflict would occur when doing this, or if other people suggested a different way.. Specifically talking around middle of the page under
 "Mandriva Installed with Windows; Looking to try another Linux Distribution"

Also was wondering about a 2g swap, Ive read stuff about it but would I really need it?
Thanks

---

### Post by TBABill on 2010-11-10
Many Dell computers use a Broadcom brand wireless device. Unfortunately they require a driver to be installed after the install. The ONLY distro that provides that driver out of the box that I have found is PCLinuxOS. With Mandriva or Ubuntu you will have to get that driver post-install. With Ubuntu, simply do the install but make sure you can plug into a router so you can download updates and that driver (by going to system>>administration>>hardware).
 
As for installing over your Mandriva installation, when you go into the install sequence in Ubuntu you are prompted where you would like to install the OS. You want to choose manual selection since you want to use an existing partition (where Mandriva is right now). Then simply select the partition where you have Mandriva currently installed and have Ubuntu install there. It will format the partition, which will eliminate Mandriva, and it will install itself there instead. Just make sure you do NOT select the partition where you have Windows installed or you will lose it and all your Windows files. If you are unsure and have the backup/recovery disk, backup your files somewhere and carefully choose the Linux partition to install to.
 
It's not a major ordeal and I do it regularly to install another distro on my test partition. I just install one over the top of whatever is there and have had few issues. Post back if you need clarification.
 
Edit: regarding 2GB swap and do you need it? Generally it's recommended. [https://help.ubuntu.com](https://help.ubuntu.com) for lots of great information when you don't see what you need here.

---

### Post by somuchdirt74 on 2010-11-10
Thank you so much, yeah I wanted to give ubuntu a try.. But I do not know what you mean by post installing the driver.  When I did found out that I wasnt able to connect to wifi I tried finding reasons for it.  But all I could really come across was about two drivers the b43 and something else I cant remember that I needed to download.  But I dont think I could find a way to download one of the drivers and when I did it hit me that I dont have a clue what to do with it or if its really even the right one.

---

