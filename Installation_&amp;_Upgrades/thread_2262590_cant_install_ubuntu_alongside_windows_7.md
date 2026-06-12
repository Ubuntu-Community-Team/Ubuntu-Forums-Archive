---
title: "cant install ubuntu alongside windows 7"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by thomas_margotta on 2015-01-26
look, im not stupid. yeah im not the most experienced with partitinoing and ubuntu, but im not mentally deficient. im trying to install ubuntu 14.04 alongside windows 7 and for some reason it does not work properly. let me explain the problem
okay, i boot from the cd and try to install it, it shows the hard drive with one partition, that is  1000204 mb, or something, 1 tb. dispite the fact i spicificly partitioned my hard drive into two partitions when i installed windows 7 so i can install ubuntu. i partitioned it into a 247 gb partition for windows 7 (because windows is annoying) and left the rest for trusty. which i had running on this before i decided, "hey, i cant play any damn games right", so you know, now im pissed. i have windows 7, the older, but better windows version, because Microsoft oft cant get their sh*t straight, installed. and now i cant use the empty space to install ubuntu, the only  user oriented operating system, because it was actually built by "we the people". please dont tell me to use some workaround, beecause windows blows. i installed windows for my leasure time, because i dont trust microsoft. im trying to install linux. what do you think the problem is here? 

i have a samsung ativ book 4 with an i5 64 bit processor that came with windows 8, which sucks. can someone please help me. by the way, ubuntu detects the whole disk as unused space. and its not, im using windows to post this now. unfortunately..... the more help the merrier!!

-csltr

---

### Post by ajgreeny on 2015-01-26
If you can boot to the ubuntu live system, please show us the output of ```
sudo parted -l
``` in terminal and/or a screenshot of gparted which will let us see exactly how your current partitions are laid out on disk and we can then tell you what is the best way forward.

This may be a UEFI vs BIOS problem as well, and the info you give will help us sort that out.

---

### Post by thomas_margotta on 2015-01-26
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                                   


the only answer i cant really give ubuntu here is, da f*uck u asking me for, but im going to say no and see what happens.


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 

 no idea what that means. lets try it again with yes

ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Model: ATA WDC WD10SPCX-55H (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 



mind you, windows runs fine. so i dont know what ubunt is freaking out about here... i had ubuntu running on this before i put windows 7 back on.

---

### Post by thomas_margotta on 2015-01-26
that partition is on the disk that it says is blank...

---

### Post by Mark Phelps on 2015-01-26
TExt posted in error ...

---

### Post by ajgreeny on 2015-01-26
> **Mark Phelps said:**
> Because ... gparted can't read GPT formatted disks.
Yes it can!

I have used **gparted** many times on my GPT partitioned disks with no problem; it's **fdisk** that will not see and be able to act on GPT partitions.

That unfortunately doesn't help thomas, and unfortunately I can't figure out what the problem is.

Or perhaps I can!
Did you make the new partitions using Windows, rather than just leaving unallocated space?  If so they may be dynamic partitions which Linux (ie, gparted, fdisk or anything else), can not see nor act upon.

If this is the situation just boot to windows again and delete those partitions in your Ubuntu space using disk-management and leave them as unallocated space.  That may help.

---

### Post by thomas_margotta on 2015-01-26
[ATTACH=CONFIG]259523[/ATTACH]
nope, its blank space.... in a forum dedicated to ubuntu, an operating system with no tech support line, i kinda thought their would be the most intelligent of individuals on here.

---

### Post by ajgreeny on 2015-01-27
Ok, next step.

From a live ubuntu system go to **Boot-Repair** in my signature and follow the instructions to run and produce a **boot-info** Report.  You will get a pastebin link which you can paste here and it may be possible to see more of what is going on and help you out.

---

### Post by thomas_margotta on 2015-01-27
[http://paste.ubuntu.com/9897581/](http://paste.ubuntu.com/9897581/)

just went to the url. understood a few words up top then got confused n x'ed out.

---

### Post by sudodus on 2015-01-27
> **thomas_margotta said:**
> [http://paste.ubuntu.com/9897581/](http://paste.ubuntu.com/9897581/)

just went to the url. understood a few words up top then got confused n x'ed out.

0. ***Backup*** before editing partitions and installing systems because it is risky.

1. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

2. ***For the installation***

See the following link and links from it:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It seems to me that you have a lot of unallocated space alongside the NTFS partition of Windows.

Boot from the Ubuntu desktop install DVD/USB drive and use ***gparted*** (a partitioning tool with a graphical user interface, easy to use) to make one partition for Ubuntu's root file system (file system ext4), and one small swap partition (no file system, but linux-swap type).

After that you can start the installer and select ***Something else*** at the partitioning window. Select the partitions that you created with gparted.

---

### Post by thomas_margotta on 2015-01-27
it says the entire disk is unallocated space, which it is not. so if i install it on the disk, which actually has something on it, then windows will not boot, because it will not exist anymore. i tried the "try before install" then install, and just going straight to install, and both show only a disk filled with unpartitioned space and no windows partition. so if i install on it, it overwrites windows. i need a dualboot of windows 7 (already intalled) and ubuntu (wont detect any other partitions so my only option is to write over everything.

---

### Post by sudodus on 2015-01-27
Are we talking about the same information? I'm talking about your attached picture in post #7.

Your uploaded data at [http://paste.ubuntu.com/9897581/](http://paste.ubuntu.com/9897581/) indicates there is nothing where we know there is Windows. Probably Windows is hibernated (not completely shut off) and in such cases it is made unreadable for other operating systems, which is good, because editing partitions or writing files in a hibernated state would damage the file system severely.

---

### Post by thomas_margotta on 2015-01-27
windows is not in hibernation, it is off. and i have a 1tb hard drive. the empty space is the entire hard drive isnt it? if i write to that partition it will ignore windows, and destroy it in the process. and windows does work, im using it now. its on a 247 gb partition. if the free space is 1000204 mb then how is it possible that there is two hundred some-odd partition outside that amount somewhere? im trying to dualboot windows 7 AND ubuntu not delete windows and put ubuntu on by itself.

---

### Post by sudodus on 2015-01-27
1. Windows has a kind of semi-hibernation, that I think should be shut off for dual booting. I used it to make it possible to shut down Windows 8 completely, and after that it works much better with dual booting Ubuntu and Windows.

This link explained how to find the setting to really shut down Windows 8, hidden deep down in the menu stack

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

I hope it is still working according to the link.


2. You should install Ubuntu in the same mode as Windows, UEFI or BIOS, in order to dual boot.


3. There might be some error in the NTFS file system, that stops linux from recognizing it. That can be fixed from Windows with

```
chkdsk /f 
``` or with the corresponding GUI tool. So try to repair the NTFS file system and check if linux can recognize the partition after that.

---

### Post by thomas_margotta on 2015-01-27
those options do not exist in windows 7, also after looking through settings i confirmed that hybrid sleep mode is indeed off. in advanced power settings, under sleep, hybrid sleep is turned off. i remember turning that off so i could enable the use of hibernation. which was not on when i tried to install ubuntu, the computer was completely powered off. however just to humor you, i will completely disable it before i restart my computer.

---

### Post by thomas_margotta on 2015-01-27
nevermind, here is a picture, you cannot disable hibernation after disabling hybrid sleep mode. however i can just turn it off. which i have been doing.

---

### Post by LostFarmer on 2015-01-27
from your post #3:> ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.  at one time the hdd had gpt partitioning but later incorrectly converted to MBR, the last 32 sectors of hdd was not zeroed (backup GPT data).  When that happens linix partitioner does not know what to do with hdd and no partitions will be listed.

To fix, I have never used program.  [http://www.rodsbooks.com/fixpart](http://www.rodsbooks.com/fixpart)


edited. when I copyed , did not get it all should be: [www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixpart")

edit #2: some reason the link still does not work, but it is correct .  do not know just what is wrong with it.  If one copys it to the address bar then it works for me.

---

### Post by thomas_margotta on 2015-01-27
found a solution. i have downloaded minitool partition wizard 9.0. ill make the partitions on windows with it. thanks for the broken link. jesus h christ.... if you dont wanna help just say so, you dont have to be a jerk about it....

---

### Post by oldfred on 2015-01-27
You had an UEFI install that uses gpt partitioning. Then you installed Windows in BIOS mode that has to have MBR partitioning. But Windows does not correctly erase all the old gpt data on drive and Linux tools then get confused on whether you have MBR or gpt and assume you have to erase drive to correct it.
The Linux tools to fix the issue is to use fixparts.

But you should also boot system and install all systems in the same boot mode. Not critical if both are BIOS/MBR or both UEFI/gpt. 
But there are some slight advantages to gpt (like a backup partition table) and UEFI (like faster booting). BIOS/MBR is only 35 years old and not best for newest hardware, but still works.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by thomas_margotta on 2015-01-27
okay. i made two partitions, then used fixparts or whatever, i installed it. i set a 600g or so partition as root, then set like 60 or 80 gb or someshit as swap. it booted to windows. what did i do wrong here?

---

### Post by thomas_margotta on 2015-01-27
okay, tried boot-repair
[http://paste.ubuntu.com/9906722/](http://paste.ubuntu.com/9906722/)
christ...

---

### Post by thomas_margotta on 2015-01-27
posting this from the ubuntu partition. gonna install some updates then check the windows partition. THANKS! F*CK WINDOWS!

---

