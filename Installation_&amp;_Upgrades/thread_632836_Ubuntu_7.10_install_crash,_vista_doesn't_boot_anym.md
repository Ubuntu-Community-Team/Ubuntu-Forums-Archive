---
title: "Ubuntu 7.10 install crash, vista doesn't boot anymore"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by oho on 2007-12-05
I tried to install Ubuntu 7.10 on my laptop on which  vista and ubuntu 7.04 where installed. I booted from ubuntu 7.10 live cd, clicked install, chose manual partitioning, there where 3 partitions listed -ntfs,ext3 and swap. I clicked the format ext3 partition option, than pressed forward. Install started to format and install files but at one moment **crashed**. Live session still worked, so i just clicked shut down the computer button. I than started it again and all i got was "Missing operation system._". No vista, no ubuntu.

I booted from Ubunto cd again,it shows ntfs partition and all files on it, i tried to open text files in OpenOffice it and it worked. Partition structure in GParted looks like:

**Partition-----------------Filesystem-----MountPoint-------Size---------Used--------Flags**
Unallocated space.........unallocated.................................1.00MiB.......87.44GiB
/dev/sda1.......................ntfs............. /media/disk............90.44GiB
/dev/sda2........................ext3.......................................20.41GiB.....500.23MiB.....boot
/dev/sda3...................extended....................................949.15GiB



There´s a picture of padlock by ntfs and extended entries.

First thing what i want is to boot somehow into vista, that i can backup my precious documents to dvd-s. (i dont know how to do that with ubuntu live cd, since u cannot put it out of dvd played while session runs,unfortunately i have no external HD-s)

Tried to run Vista installation cd, clicked Repair, System recovery Options window appears, "Select an operating system to repair and click Next", but none is listed. I clicked Next, some System recovery options appeared, tried Startup Repair and got back that "Windows cannot repair this computer automatically".
Than i tried with command prompt and bootrec:

X:\Sources>bootrec /ScanOs
i got back:
"Total identified Windows installations: 1 
[1]  C:\Windows
The operation completed successfully.
"

Next thing i tried was:
X:\Sources>bootrec /RebuildBcd
I got back:
"Total identified Windows installations: 1
[1]  C:\Windows

Add installation to boot list?"  
I wrote Y, the answer was:
"The volume does not contain a recognised file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted."

Than i tried what was written in microsoft support page for bootrec:

1.bcdedit /export C:\BCD_Backup
I got " The store export operation has failed. The system cannot find the file specified."

2. c:
Went ok.

3. cd boot
Went ok.

4. attrib bcd -s -h -r
Went ok.

5. ren c:\boot\bcd bcd.old
Went ok.
6.bootrec /RebuildBcd
Got the same ansver as previous time:
"Total identified Windows installations: 1
[1]  C:\Windows

Add installation to boot list?"  
I wrote Y, the answer was:
"The volume does not contain a recognised file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted."

If i write DIR it nicely lists directories of c:\ with a remark that a volume in drive C has no label.

I tried also:
bootrec /fixmbr
ok.

bootrec /FixBoot
I again got: "The volume does not contain a recognised file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted."

:confused: ....I need help.

---

### Post by confused57 on 2007-12-05
If you have a Gb or more ram, which you probably do since you're running Vista, the Knoppix live cd can be run from ram, which will free up your DVD drive to copy files...see the toram cheatcode here:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

Added:  You might also want to read this link on testdisk:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

The gparted live cd may be the easiest way to run testdisk.

---

### Post by oho on 2007-12-05
Sorry i made a huge mistake in Gpart partition table, the correct one is:

**Partition-----------------Filesystem-----MountPoint-------Size---------Used--------Flags**
Unallocated space.........unallocated......................... ........1.00MiB
/dev/sda1.......................ntfs............. /media/disk............90.44GiB.......87.44GiB
/dev/sda2........................ext3............. ..........................20.41GiB.....500.23MiB.. ...boot
/dev/sda3...................extended.............. ......................949.15GiB

---

### Post by oho on 2007-12-06
Thanks **confused57**, i went for **Knoppix 5.1.1 Live cd** and **TestDisk** , one of the options applied helped, though i don't know exactly which one... 

I'll write down the procedure, it might help also some other newbie with the same problem.

After booting from Knoppix cd (no cheat codes), TestDisk of course didn't  work on the first shot. Googling I found this solution:

Open Root Shell
Type in: passwd
Invent some password quickly and remember it
Than type:
cd /usr/lib
ln -s libntfs.so10.0.0 libntfs.so.9
sudo testdisk

I ran *Analyse*, but for TestDisk everything seemed to be ok (Structure: ok)

First i tried to "Write TestDisk MBR code to first sector" , after restart u get "TestDisk
1234F:" on the screen. Typed 1,  the thing called Windows Boot Manager which yelled back at me "File: \windows\system32\winload.exe
Status: 0xc000000e
The selected entry could not be loaded because the application is missing or corrupt."
 

Than I ran Knoppix+TestDisk again , and tried to  Rebuild NTFS Boot Sector on NTFS Partition, because that was the only option where TestDisk showed some mismatch. 

Repair NTFS MFT spat out something like *Segmentation fault*, that happened also if i try to list files and directories In TestDisk on ntfs partition.

I also ran **Gparted** and deleted all ext3 and swap partitions (u have to unswap and unmount them first)
Than i rebooted the computer with **Vista DVD** went to Repair and again tried **Startup Repair**, but this time _it worked_ (There's a warning sign that it might take a few minutes, but it took much more than half an hour with no info what was going on and it declared the success just a fraction of a second before me clicking the cancel button)


I don't understand how the 1MB of unallocated space appeared in front of NTFS partition after the Ubuntu **Gutsy** installation crash. It was not there before and after Vista DVD Startup Repair sweating it disappeared.

Before the Knoppix success, i tried to install Gutsy once again , this time it crashed after 90% of installation was done (first time the crash came after 25%, i think). 
I dont know if I dare to try again,  might rather wait for next edition (had no trouble with 7.04 on this computer). Better not going into Gutsy installation on computer with Vista partition without backing up all your files.

**btw.** The comp is Gericom 17120 Laptop , 2GB of memory, Pentium core duo T2080 1.73Ghz,Nvidia Go 7300,120GB HD , also has some Vista issues - if u don't install drivers in exact order, things get messy, so no driver upgrading without reinstaling the whole Vista...

---

