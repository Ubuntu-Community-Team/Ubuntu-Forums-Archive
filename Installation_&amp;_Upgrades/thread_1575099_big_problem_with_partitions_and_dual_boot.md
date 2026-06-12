---
title: "big problem with partitions and dual boot"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by nononano on 2010-09-15
Hello everyone!

I have tried a lot to fix my problem but, since I have not found solutions in the forum, I have decided to make my own post. Four days ago I have decided to upgrade from Ubuntu 9.04 to 9.10 and then to 10.04. The step between 9.04 to 9.10 created many problems that I hoped would be fixed in the subsequent step. The second step instead made worse and compelled me to reinstall Ubuntu. The point is that I have also Windows 7 in my laptop and I don't want to loose it. Thus I tried to download the disk of Ubuntu 10.04 in order to install it from scratch preserving windows. The problem is that when, in the installation, I have to use gparted to specify in which partition Ubuntu should be installed gparted itself doesn' recognize any partition. From the perspective of gparted there are no partitions and no OS in my laptop.
[IMG]http://www.spaghettifile.com/viewtrack.php?id=739117[/IMG]
the situation got even worse when i tried to run a tool called "testdisk" hoping that it would have fixed this problem of the partitions. At the end of the day I told testdisk to rewrite the partition table and the MBR and now I'm not even able to boot neither the messed up version of Ubuntu nor Windows 7. The only good thing is that I'm able to access the data of Windows and Ubuntu through the LiveCD. When I try to boot (using grub) Ubuntu I get this error:
```

Error 15: File not found

```
and when I try to boot Windows I get the following:
```

Error 13: Invalid or unsopported executable format

```

The output of the command "fdisk -l" is
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+   6  FAT16
/dev/sda2              13        4190    33559785    c  W95 FAT32 (LBA)
/dev/sda3           18401       29594    89915392   83  Linux
/dev/sda4           29595       30402     6490260    f  W95 Ext'd (LBA)
/dev/sda5           29595       30074     3855560   82  Linux swap / Solaris
/dev/sda6           30075       30402     2620416    c  W95 FAT32 (LBA)

```
If anyone knows what should I do to solve my problem I would be very grateful! Thanks!!

---

### Post by nahrees on 2010-09-15
I have had the same issue for ages, albeit with 9.10 and XP. I'd also be very interested in a solution.

---

### Post by rtrask on 2010-09-15
As a disclaimer, I have not had this specific problem. I have started with a clean install of Windows 7, and then installed Ubuntu afterward. But here is how I would approach your issue.


I've had issues with the gparted that comes with 10.4. What I have done is to boot with a 9.04 install disk (use the "try without changing system" option) and then use the gparted to set up the partitions. When that is done, just reboot to one of the 10.04 installation disks. select specify partitions manualy options.

I think you might be better off to use the alternate installer version, and select the rescue a broken system option. 

So I have

---

### Post by nononano on 2010-09-15
First of all thank you very much for the reply! Second, do you think that it is a problem of the Ubuntu 10.04 installer? I could try to burn a new cd with the previous version but actually I have tried to run the windows boot recovery from the windows 7 disk and also that one does not recognize any OS. I suspect that it is a problem related with the partition table and MBR. Anyways I could also follow your kindly advice!

---

### Post by nononano on 2010-09-15
Another interesting info is that giving the command "sudo cfdisk /dev/sda" I get the following error:
```
FATAL ERROR: Bad primary partition 3: Partition ends after end-of-disk
```
if I find the way to work it out maybe I would solve my problems!

---

### Post by oldfred on 2010-09-15
I would suggest going back in with testdisk. It should see the partition error and let you repair it. 

Gparted will not work on drives with errors. Often it is windows needing chkdsk but it can be overlapping partition entries or your beyond end of disk.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

