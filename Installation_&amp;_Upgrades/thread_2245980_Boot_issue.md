---
title: "Boot issue"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by cook1965 on 2014-09-27
Here is my issue. I have tried installing Ubuntu from Wubi and everything seems to install great, but when I restart my computer, I get an error message about missing the boot mgr. I use to be able to dual boot from my windows 7 machine, I even tried partitioning my second hard drive, but I still get the same error message about a missing boot mgr. 
What am I doing wrong?
Oh, and recently I had to replace my motherboard, so I reinstalled windows 7, and since that reinstall it seems all my problems started.
Thank you
George

---

### Post by Bashing-om on 2014-09-27
cook1965; Hello;

Upfront; WUBI is no longer supported at all.
Is this new mother board:
> 
Oh, and recently I had to replace my motherboard, 

UEFI ? .. as that was the demise of WUBI. WUBI can not function in that booting method.

[INDENT][INDENT]just my 2 bits worth
[/INDENT][/INDENT]

---

### Post by cook1965 on 2014-09-27
yes, new motherboard. What I'm thinking is there is a problem with my windows 7 install,

---

### Post by Bashing-om on 2014-09-27
cook1965; Hey, hey.

What is at question here is if the new motherboard is UEFI ?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Otherwise, others with the greater experience with Windows/WUBI will have to advise.

[INDENT][INDENT]sometimes I hide my head in the sand
[INDENT][INDENT][INDENT][INDENT]just do not want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hakuna_matata on 2014-09-27
> **cook1965 said:**
> I have tried installing Ubuntu from Wubi and everything seems to install great, but when I restart my computer, I get an error message about missing the boot mgr.

> **cook1965 said:**
> 
Oh, and recently I had to replace my motherboard, so I reinstalled windows 7, and since that reinstall it seems all my problems started.

It is possible to install Windows 7 in UEFI mode, but Wubi needs old BIOS mode. Maybe your BIOS or firmware offers an option "UEFI & legacy BIOS". This could be a solution.

Another possibility is to use Wubi with an UEFI boot loader: [http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598](http://ubuntuforums.org/showthread.php?t=1639198&page=121&p=13121598#post13121598)

---

### Post by oldfred on 2014-09-27
One of the main advantages of wubi was that you did not have to repartition drives. And Windows 7 standard installs from vendors almost always used all 4 primary partitions with MBR(msdos) partitioning. And wubi was never intended for long term installs. It was a longer test install to see if a user like Ubuntu enough to do a full partitioned install. Now you can actaually do a full install to a flash drive and use that for a longer test.

But if you have two drives, best is to have Windows on one drive and Ubuntu on the other drive. And many suggest disconnecting the other drive when installing. Both Windows & Ubuntu have some settings that may install parts to the other drive if not aware before or during install.

And with the very new UEFI systems, you have both UEFI and BIOS boot modes before you even start anything. And for both Windows & Ubuntu how you boot install media, DVD or flash drive is how it installs. And both systems need to be UEFI or both BIOS to make it easy to manage.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

