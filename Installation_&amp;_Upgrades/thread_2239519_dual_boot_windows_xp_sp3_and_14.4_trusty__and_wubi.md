---
title: "dual boot windows xp sp3 and 14.4 trusty  and wubi"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by joe129 on 2014-08-14
hello just finished a reinstall of 12.4.3 after a failed 14.4.1 upgrade  attempted that took over 24 hours,

 I have a dual boot system( via wubi)  win xp3 on a c: 160gb drive and ubuntu 12.4 installed on f: 500gb drive  4gb ram amd64  ubuntu on a 30gb install size .   

I have what I consider is a simple  question does 14.4 support a dual boot config via wubi for windows xp sp3 .

 I have been  using ubuntu for over two years I have some understanding of it throuhgh  trail and error all my files are backed up in multiple  location in 4  different clouds so it doesnt really matter if this pc falls over as I  have three laptops to use all backed up to 4 clouds.  

 I would like to  install 14.4 as part of a dual boot xp sp3 system, I have some old  legacy programs dependant on xp sp3,  I have vista and win7 pro on  laptops.

is it possible to configure my F. drive soley for ubuntu and still have win xp sp3 on the C. drive?

---

### Post by kc1di on 2014-08-14
Hi Joe129 and welcome to the Ubuntu forums,

I'm not sure I can answer your question, but believe support for WUBI installs was dropped in 13.10 or something like that. 

If your running xp on that machine- it's most likely quite old for 14.04 and 12.04 lts is supported until 2017 , I think I would stick with that 
but if you want to try 14.04  I'd do a complete dual boot install and not mess with wubi . 

good luck :)

---

### Post by Mark Phelps on 2014-08-14
> does 14.4 support a dual boot config via wubi for windows xp sp3 .

Ubuntu 14.4 does NOT support Wubi.  Not to say you can't force an install using Wubi, but you'll then be using an unsupported product (Wubi) and if there are problems, you're basically then out of luck.

---

### Post by grahammechanical on 2014-08-14
When we use wubi.exe to install Ubuntu were are in fact installing Ubuntu inside Windows. If Windows breaks then you will not have access to Ubuntu. And you are using Windows XP which itself is no longer supported by Microsoft.

A better choice would be to do a dual boot with XP and Ubuntu. Then you will have two independent OS and when one breaks or becomes infected with malicious code (XP) you can boot into Ubuntu. You will still have a working computer.

This upgrade from 12.04.3 to 14.04, was Ubuntu a wubi install? Upgrades from 12.04 to 14.04 do take a long time. I did one yesterday. It was almost twice as long to a new install. But the option of installing with wubi.exe was never meant to be long lasting. It was a try out Ubuntu method without re-partitioning the hard disk. If satisfied with Ubuntu then the intention was for the user to do a proper dual boot. I am not surprised the upgrade failed.

Regards.

---

### Post by oldfred on 2014-08-14
If you have wubi in the f: drive or really another partition, then you can install Ubuntu fully into that partition and dual boot with XP. But you would have to backup wubi before hand.

You also need to see how many primary partitions you have used. MBR(msdos) only has 4 primary partitions, but one primary can be converted to an extended partition which then just is in effect a container for as many logical partitions as you want. XP only boots from primary partitions, but Ubuntu can use logical partitions without issue.

Are you running Ubuntu or one of the other flavors as kc1di mentions, older hardware does not run Unity well. I have full Ubuntu but use gnome-panel/fallback/flashback to have the old menu structure. That does also run on older systems as does Lubuntu or Xubuntu. 

Download live installer and post this from terminal. Or if wubi still works post from that.
sudo  parted -l
sudo fdisk -lu

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

