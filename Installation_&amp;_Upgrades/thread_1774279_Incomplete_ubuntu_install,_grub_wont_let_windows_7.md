---
title: "Incomplete ubuntu install, grub wont let windows 7 run"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by ignacio69 on 2011-06-03
Dear sir,
I am myself a happy user of Ubuntu.
I wanted to solved the problem of Windows 7 not being able of connecting to internet by installing a dual boot Windows-Linux

In a HP-G62-a50SS with Windows 7 Home Prem OA I tried Linux distribution ubuntu 8.04 LTS.
Linux distribution Ubuntu went wrong and did not finish. Exit at step before asking for root name and password.
After rebooting, Recovery Manager in Windows (disk D that start when there are problems in C:) says 0x0ef0009 "null input string"
After searching in the net one of my possibilities is to order the Recovery Kit from HP
My question:
how to know using a Live CD and console if I made a resize of the old C: Windows disk?
how to know using a Live CD and console if I made a format of the former C: Windows disk?
does anybody how to guide me (in order not to mess up more) using the Live CD to recover the C: windows disk?
is this theoretically possible.

M.

---

### Post by Hedgehog1 on 2011-06-03
**Fix MBR:** To get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):

[IMG]http://img24.imageshack.us/img24/3200/fixmbr01.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:

[IMG]http://img848.imageshack.us/img848/1335/fixmbr02.png[/IMG]

[IMG]http://img802.imageshack.us/img802/7531/fixmbr03.png[/IMG]

[IMG]http://img803.imageshack.us/img803/530/fixmbr04.png[/IMG]

```
bootrec /FixMbr
```


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-06-03
You can use an Ubuntu CD/USB to install a Windows-like bootloader.

From a terminal on the LiveCD/USB (Applications > Accessories > Terminal), run the following commands:

```
sudo apt-get install lilo

sudo lilo -M /dev/sda mbr
```


You attempted to install 8.04 LTS.  10.04 LTS is the current support LTS for Ubuntu.  I wonder if that would install better for you?


***The Hedge***

:KS

---

### Post by ignacio69 on 2011-06-18
Hello,
I have already solved the problem
I would like to share with others the solution.
What is has to be done is to make the partition where was windows, C:, to be NTFS
there are several ways to do it:
A) what I did:
1) what I did; take out the HDD and with the help of a Windows application like Partition Magic or something like that convert the partition to NTFS.
2) start Recovery that is installed in D:
3) at the end, you have the computer as it was when left the factory.
B) what is said in the forums that can be done
1) If you do not have the program or the possibility to take out the HDD, you can try to use ubuntu to repair it.
2) as Hedgehod sugested using a LIVE CD, is theoretically possible with the help of GParted or a similar program (maybe it will work fdisk also) to convert the affected partition to NTFS. (I am just not sure if writting the MBR would be a proble later on to make the recovery)
3) once the partition is a NTFS you can start the recovery from D:
4) result: you have a factory setting computer.

Further explanation:
Before starting the ubuntu installation I made a backup of all the data documents, excel tables, and other personal files using a DVD.

Now that is solved, I can explain what went wrong during the installation, why and how to avoid it in the future.

What went wrong:
When Ubuntu started the installation and got to the step of the where to put the home partition in your computer, I chose C: and resize it (decrease windows to use the free space in C: for ubuntu); however the installation was aborted by a error and I had to quit the installation and reboot. when I reboot the computer instead of a NTFS partition with C: in it, I had a ext 3 not finished partition and that is why windows could not start not either D: as a recovery.

why went wrong:
even as it is theoretically possible to resize the disk during installation, specially windows 7 does not like linux and did not work; 

how to avoid it:
it is wiser to make the partition within windows using a windows program to make a partition using the free disk space to put your future linux partition.

So, If you want to share windows 7 and linux
1) make a partition using a windows program for you future linux partition
2) insert the installation CD
3) shut down windows and computer
4) switch on your computer, ready to get into the booting menu, 
5) select boot from CD/DVD
6) follow the instructions
7) when you get to the step "where to put the linux partition", choose the one created before with the windows program. You can recognize it by the size you chose.
8) follow the installation steps further
9) enjoy you dual boot up windows -linux computer.

---

