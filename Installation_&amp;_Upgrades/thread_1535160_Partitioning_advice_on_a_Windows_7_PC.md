---
title: "Partitioning advice on a Windows 7 PC"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by ptrinder64 on 2010-07-20
Hi people,
 
I’ve recently bought a new laptop with Windows 7 on it which I would like to install Ubuntu on. Whilst I have dabbled in disk partitioning before, I have hit a bit of a brick wall on this one and would be grateful for any advice.
 
Basically I want to have a Windows 7 partition, a separate Ubuntu partition, a separate OpenSuse partition and of course a swap. In an ideal world I would also like to have a separate Home partition too. Unfortunately the laptop’s factory setting already includes 4 primary partitions – System, Windows 7, Recovery, and HP_Tools (which I believe just contains tools for HP system recover - [http://h30434.www3.hp.com/t5/Operating-systems-and-software/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428")).
 
Now what I’m really after is advice on whether setting up the partitions as I want is possible, and which partitions you would recommend removing. I’m loathe to removing the Recovery partition as the laptop didn’t come with a Windows 7 DVD, but can see this  as one of the obvious choices to ditch. I’m guessing I then have to make an extended partition with logical partitions, but am not sure if this is right.
 
So any advice? Should I quit with Windows still on it or is it unlikely to be resolved without formatting the disk and starting from scratch?
 
I haven’t even thought about GRUB yet…
 
Thanks for any guidance offered!

---

### Post by pricetech on 2010-07-20
First thing I'd do is pitch a "hissy fit" with HP for not including media.

Second thing I'd do is see if there is a recovery disk creator somewhere in the programs menu.  That should let you create a recovery disk.

Failing that, create a Windows PE disk using the free tools from Microsoft and stash the WIM file on an external hard drive or network share.

Only after you have obtained or created a recovery disk should you begin monkeying with partitions.

You probably have a small partition at the front of the drive, 100 megs or so.  Leave that one be.

Copy the tools from the utility partition to external media, or download a fresh copy of them if that's an option, then you can wipe that partition.

Once you have the recovery media mentioned above, wipe the recovery partition.

You probably won't gain enough drive space to install the other OSs so you'll want to downsize your Windows OS partition.  Do this in Disk Management in Windows.  Defrag first and reboot a couple of times afterward, letting Windows do any disk checking it wants to do.

Install your other OSs in whatever order you want using the drive space you have made available.

How big to make your partitions for each is up to you, but splitting the drive into three equal parts for three OSs makes sense.

---

### Post by oldfred on 2010-07-20
I agree with pricetech except I only make 20-25GB for system partitions and put all data into separate partitions. Originally I just had a NTFS shared partition for data I wanted in both Win & Ubuntu like firefox profiles, thunderbird profiles & photos. I was easier to convert spouse as then the main applications were essentially the same with the same data in both systems. Now I have most data in ext3 partition as that data does not have to be shared with win.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Goolie on 2010-07-20
Well, my laptop had the same situation, but I just scrapped windows altogether. Make the windows recovery cd like above if you want to have that available.  When I was bigger on windows I didn't 
use recovery cd's as such.  I used Norton Ghost to create a complete back-up.  So in actuallity I never scrapped Windows.  It's on my external hard drive.  All I'd have to do is pop in the Ghost CD
and put Windows back on, same OS, files, documents, everything from the day I made that back-up.

---

### Post by arsenic23 on 2010-07-20
You should be able to purchase windows discs from Microsoft for about $12 or so ( or that used to be the price per disc ):  [http://support.microsoft.com/kb/326246](http://support.microsoft.com/kb/326246)


Purchase, download, or copy a windows disc that works with your license and then delete that recovery partition.

---

### Post by linux18 on 2010-07-20
Yeah what everyone else said except for two steps:

1. defragment
2. backup
3. remove unnecessary partitions
4. resize windows partition
5. make sure windows still works - maybe some disk checking
6. install ubuntu without installing grub - this is my secret recipe
7. boot into windows again with disk ckecking
8. use the ubuntu live cd to install only grub " sudo grub-install && sudo update-grub " - also part of my secret recipie
9. try booting into both OS's

---

### Post by pricetech on 2010-07-20
> **Goolie said:**
>  I used Norton Ghost to create a complete back-up.

The MS tools are a free download. No cost involved.  There are Open Source tools as well, but if the user is new to Linux he / she might find it easier to use an MS solution.

> **linux18 said:**
> Yeah what everyone else said except for two steps:

6. install ubuntu without installing grub - this is my secret recipe
8. use the ubuntu live cd to install only grub " sudo grub-install && sudo update-grub " - also part of my secret recipie

Could you elaborate as to why ??  Just curious.

---

### Post by linux18 on 2010-07-21
> **pricetech said:**
> 


Could you elaborate as to why ??  Just curious.
By not installing grub and ubuntu at the same time, you can avoid problems with windows complaining, disk checking before a grub install prevents windows 7 from going into recovery mode on next boot ( and take forever to boot "normally"  )

---

### Post by pricetech on 2010-07-22
> **linux18 said:**
> By not installing grub and ubuntu at the same time, you can avoid problems with windows complaining, disk checking before a grub install prevents windows 7 from going into recovery mode on next boot ( and take forever to boot "normally"  )

K.  Thanks.  I haven't had the issue, but then it's been some time since I dual booted.

---

### Post by rawlins02 on 2010-07-22
I also in the process of setting partitions for dual boot Windows 7 and Ubuntu 10.04.  Tried to set partitions using the Ubuntu 10.04 install. Wouldn't let me set 100 MB for /boot, saying size is less than minimum.  Now following advice in this thread using the Windows Disk Management tool. Questions:  I've written my recovery disks. Why is is so important to wipe recovery partition?  It's only 8GB and I have 460 GB disk.  Also, the tool is telling me minimum I can shrink the main OS(C:) partition to is 228 GB. I'd wanted Windows to be only about 100 GB, and want to set the most for linux. Lastly, does the new partition for linux get set in here.

---

### Post by oldfred on 2010-07-22
While this discusses Vista it is the same for 7.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)


You can use gparted but have to be sure on the checkbox.
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by rawlins02 on 2010-07-22
I've downloaded Partition Wizard. Seemed to handle reducing size of C drive. I then deleted the Recovery partition. Now it won't boot to Windows. I just put in the recovery disks that I'd created, some odd error came up.  This has gotten interesting... Hope I can get back the factory Windows OS.

---

### Post by rawlins02 on 2010-07-22
Thanks for the pointer to that how-to, oldfred. I've successfully got back to the factory Windows 7 installation using the recovery disks I'd created. Will give this a shot again tomorrow.

Mike

---

### Post by ptrinder64 on 2010-08-15
Apologies to all - I think I forgot to subscribe to this thread that I started! 

Thanks everyone for the help. What I ended up doing was backing up (of course!) and deleting the HP_Tools partition. I then resized Windows 7 down and created an extended partition with a boot, swap, and three EXT4 partitions (two 25mb partitions for OpenSUSe and Ubuntu, and a larger one for the /home/ folders). I managed to install everything fine. There are a few issues now (such as my Ubuntu has disappeared from Grub) which I believe has arisen from effectively installing OpenSUSe afterwards which uses Grub instead of Grub2, however I shall not go into it on this thread. 

Now to sort out those problems and the rather large one on my main PC...

Forgot to mention - very useful information on the Windows 7 CDs...

---

