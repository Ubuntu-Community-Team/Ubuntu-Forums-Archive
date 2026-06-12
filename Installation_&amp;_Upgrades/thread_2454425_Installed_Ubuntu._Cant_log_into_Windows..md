---
title: "Installed Ubuntu. Cant log into Windows."
date: 2020-11-29
forum: Installation &amp; Upgrades
---

### Post by jbader12 on 2020-11-29
Hello All!
A few days ago, I installed Ubuntu on my HP desktop and followed all the directions. I intended to have a dual boot computer with Ubuntu and Windows.
After all that hardwork , I am unable to log into windows in the grub menu. I see a message that says "Can't find command drivemap" "Invalid EFI file path." 

I tried a **lot** of options found on ubuntu forums on the internet.

I can confirm that when I was installing Ubuntu, I created the partitons on the largest available free space on the disk ( 930 MB). I am unsure if that contributed to the issue. The installations instructions did indeed say to pick a large free space. I can also confirm that I might have gotten confused while creating the EFI. Now I see /EFI and boot/efi. I am unsure if I there are supposed to be 2 EFI partitions. The link below will show you the screenshot with the 2 EFIs.

I am kinda fed up now. 

Can some one please tell me how I can just recover all my windows files and programs?

I dont care about reinstalling/ recovering windows. I can just buy a new computer.
I dont care about reinstalling/ recovering Ubuntu. 
I dont care about recovering and Ubuntu files either. 

All I care about is recovering my windows files and programs.

I appreciate your time and effort.

JB

[https://ibb.co/k55WjBH](https://ibb.co/k55WjBH)
[IMG]https://ibb.co/k55WjBH[/IMG]
[IMG]https://ibb.co/k55WjBH[/IMG]

---

### Post by ajgreeny on 2020-11-29
The information in the image you attached suggests that your Windows installation is now no more; gone; nada, so I'm afraid if what you showed is all you have, restoring your Windows data files is going to be extremely difficult.

Just to be certain please run command ```
sudo fdisk -l
``` in terminal from your installed Ubuntu and copy back here using code tags please by pasting the text from the terminal into your reply, highlighting it and clicking the # icon the toolbar.  If you use the **Post Quick Reply** simply type [noparse]```
 at the start of pasted text and 
```[/noparse] at the end of it including the square brackets.
There is also a "How to" in my signature below.

---

### Post by jbader12 on 2020-11-29
Here are pics of sudo fdisk -l

[https://ibb.co/k3vHr6T](https://ibb.co/k3vHr6T)

[https://ibb.co/dDfv3c4](https://ibb.co/dDfv3c4)

---

### Post by oldfred on 2020-11-29
You erased Windows.
Ubuntu install does not use as much space as Windows, but whatever files you installed overwrote some Windows files & data.
You always have good backups, drives fail, users make mistakes and "stuff" happens. 
We assume if you do not have backups your data must not be important.

Some that use Windows say Windows tools may work better.
I have used photorec (before I had better backups). It only recovers files by extension or type, not full file name. And you must have another drive of similar size to restore data into.
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

This is now older, have not seem much from the Windows users on newer info. You can try a Windows forum.
Windows free recovery software - new 2020 Supports NTFS, FAT, exFAT and ReFS file systems
[https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/windows-file-recovery/9n26s50ln705?activetab=pivot:overviewtab)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.
If NTFS partition can be mounted, even read only:
[https://ubuntuforums.org/showthread.php?t=2422604&page=2](https://ubuntuforums.org/showthread.php?t=2422604&page=2)

---

### Post by mastablasta on 2020-11-30
no wonder it was hard work. you managed to make 9 linux partitions + and efi partition. there should be only one by default (maybe 2 with uefi boot). even if you added /home and /swap as partition that would make it 4. you have 9. sometime si wonder where people find these "*tutorials*"

---

