---
title: "Wanting to install Ubuntu Netbook 10.10 on Asus EEE PC 1001P"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by gaiamuse on 2010-10-26
Hi,

I am trying out the new Ubuntu 10.10 netbook on a USB stick and love it! 

Asus EEE PC 1001P
I would like to install this but have queries from some of the threads that I have read.
In Disk Management
Partitions:
This ASUS comes with four partitions
1. C 80.00GB which is XP
2. D 62 GB
3. PE Partition almost 7 GB which I assume may be XP recovery
4. EFI system partition - not sure what this is

All four have the blue lines - primary on them.

From reading the threads, I understand that there can only be 4 primary partitions. I wish to keep XP and the recovery. This also comes with boot booster and ASUS Express Gate.

I would like to know what would be the easiest way to proceed for a newbie. Would installing ubuntu side by side with XP still be possible when there are 4 primary drives? 

Would appreciate any help.

Many thanks and cheers,

gaiamuse

---

### Post by movieman on 2010-10-26
If the disk uses an MSDOS partition table (like almost all current PCs) then four partitions is all it can handle. But if you can live without the d: drive you should be able to delete that partition and create an extended partition in the same space for Ubuntu to install into.

---

### Post by gaiamuse on 2010-10-26
Hi,

Thank you for your prompt response! I would like to know why not choose the option to install along side other operating systems? What does Ubuntu do when this is chosen? Does this mean if the computer has 4 primary partitions that option would not work? For someone new at installing Ubuntu, the partitioning approach seems complicated [partly due to the computer manufacturers setting the drive to 4 primary partitions]

cheers,
gaiamuse

---

### Post by movieman on 2010-10-26
If you have four primary partitions then that's it: that's all that the MS-DOS partition table supports, because it was designed twenty years ago when a 40MB drive was big.

So Ubuntu can't work around the DOS limitations that continue to infest the PC decades later, and unfortunately some PC manufacturers seem to think that no-one would ever want to dual-boot a different OS on their computer. My laptop came with four primary partitions too, but fortunately two of them were recovery partitions in different languages so I could easily delete the one I wasn't going to use.

---

### Post by gaiamuse on 2010-10-27
Hi,

Thanks again for the reply. According to this: [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

Article describes what the headings mean with a ubuntu 10.10 install
********************
1. [COLOR=#008080]_Install alongside other operating systems_[/COLOR]

- Choose this option ONLY if you have another OS (e.g. Windows XP) and you want a dual boot system.
[COLOR=#00FF00][B]
Editor's Note:[/B][/COLOR] *Remember that, after the installation, the Windows boot loader will be overwritten by the Ubuntu boot loader!*

2. _[COLOR=#008080]Erase and use the entire disk[/COLOR]_

-  Choose this option if you want to delete your existing operating  system, or the hard drive is already empty and you want to let the  installer automatically partition the hard drive for you. This is the  option recommended for all users, especially those who want a machine  with a single operating system on it.

3. _[COLOR=#008080]Specify partitions manually (advanced)[/COLOR]_

-  This option is recommended ONLY for advanced users, to create special  partitions or format the hard drive with other filesystems than the  default one. But it can also be used to create a /home partition, which  is very useful in case you reinstall the whole system.
********************

My query is why can I not use the first option: install along side other operating systems. What does the first option exactly do? Will it overwrite the recovery partition? The 3 option to partition manually is for advanced users. I thought Ubunutu developers were trying to make it easier for people new to Ubuntu to install a dual boot on their system.

cheers,
gaiamuse

---

### Post by movieman on 2010-10-27
> **gaiamuse said:**
> My query is why can I not use the first option: install along side other operating systems. What does the first option exactly do? Will it overwrite the recovery partition?

As I understand it that won't overwrite any partitions, which is precisely the problem: the disk has four partitions and no free space, so the only way to install is to delete one of the partitions so that Ubuntu can create an extended partition there to install into.

---

### Post by viant on 2010-10-28
> **gaiamuse said:**
> 
1. [COLOR=#008080]_Install alongside other operating systems_[/COLOR]


This option does not appear in my screen. Anyone knows why?

---

### Post by gaiamuse on 2011-02-21
Hi,  I installed Ubuntu netbook 10.10! Finally got around to giving it a try. So now I have a dual boot: Ubuntu and Windows. Ubuntu takes most of my hard disk space. Yeah! 

A big thank you movieman!     

Viant: I had to delete the D drive as when I first tried to install Ubuntu it did not give me the option to install along side other operating systems. You may need to check the disk management and see if your system has four primary drives.      

Some things I did: 

1. I upgraded the bios as there were some issues with this version of ASUS 1001P 

2. I backed up the PE drive that has the restore to factory default on it, though this may not really work. I can live with that.   

3. I chose to install alongside other operating systems. I had to divide the disk space between Ubuntu and Windows. It took that space plus the deleted D drive. I checked with GParted. I am very happy about that.   

4. After re-booting Ubuntu, I also re-booted windows and it did a chkdisk and started up fine. Had all my network setting, software etc.  After some help here, reading some info on ASUS forums and looking at a few youtube videos, I am glad I took the plunge.    So again, many thanks to you all for such a wonderful OS. Now time to go exploring with it... :)    gaiamuse

---

