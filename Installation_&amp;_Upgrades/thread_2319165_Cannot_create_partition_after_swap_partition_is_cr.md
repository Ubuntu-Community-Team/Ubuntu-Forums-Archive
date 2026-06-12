---
title: "Cannot create partition after swap partition is created"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by Michel_Tremblay on 2016-04-01
I have Ubuntu on a computer and that is working fine. I find everything that in need by searching the net. 

Now, i'm trying to install it on a computer who has already Windows 8.1 on it for a dual boot. I have the C for Windows and a D drive for my programs, documents and all the rest. I did install some other flavor of Linux un the past without any problems. 

Noe, I already have some free space available for Ubuntu. When installing, i choose "something else" and i can see /dev/sda, the windows 8 installation partition followed the D drive and at the end the free space that i want to use for Ubuntu. 

Following instructions that i find on the net, i created a swap of 512 meg by clicking on the empty partition, after that i'm not able to create anything else it's unusable. I tried different options but i cannot get it to create the / partition, the swap and the home partition. 

What do i have to do to make it work. 

Thanks

---

### Post by oldfred on 2016-04-01
Is Windows 8 in BIOS/MBR, so 4 primary partition limit exists?
Post this:
sudo parted -l

---

### Post by Michel_Tremblay on 2016-04-01
I'll verify that and be back.

Thanks

What i know is that i have a system partition (small) on C it's Windows 8 showing as "loader" when i try to install Ubuntu, a D partition for all my files and a 197.35 Gig partition that i would like to use for Ubuntu. 

[IMG]http://i65.tinypic.com/2ykyt93.jpg[/IMG]

Sorry for the size of the picture, i did that in a hurry.

---

### Post by oldfred on 2016-04-01
Better to attach screen shots.
Easy to do with forum's advanced editor and paper clip icon.

You have BIOS/MBR.

But then you have to create an extended partition to hold logical partitions. Do not create any partitions with Windows. 
Use gparted or installer.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[URL="https://sites.google.com/site/easylinuxtipsproject/first"]https://sites.google.com/site/easylinuxtipsproject/first

[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 

[URL="https://sites.google.com/site/easylinuxtipsproject/first"]
[/URL]

---

### Post by Michel_Tremblay on 2016-04-02
Got it to work, it's installed alongside Windows and I have the dual boot screen. I don't know why but the first time I did it, it wasn't working but it's fine now. 


Have a good day.

---

### Post by Michel_Tremblay on 2016-04-03
Where do i put solved on this thread

---

### Post by howefield on 2016-04-03
At the top of the thread - Thread Tools > "*Mark this thread as solved*"

---

