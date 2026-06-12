---
title: "Installing Xubuntu permanently after trying it out"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Zickar on 2008-12-01
I've been messing around with Xubuntu for some time now but I haven't installed it yet, I just boot from a CD and choose the "Try without installation" option on prompt, the thing is I'm not sure what implications would installing Xubuntu have on my Windows because at the moment when I take the CD out and restart the computer windows starts normally, if I do install Xubuntu on my PC does taking out my CD and restarting my PC bring back Windows !! 

Another question about the Installation, I always hear people talking about partitions and how some people get ****** up foe messing around with some settings, Is the installation really easy or should I read about it first, second of all should I change anything in the settings or keep the default settings and just proceed on prompt ??

---

### Post by Dan_Dranath999 on 2008-12-01
If you install Xubuntu on your current partition (where Windows is) you'll delete windows.
That's why you should re-partition your hard disk, so you can have windows in 1 partition and Xubuntu in the other (Dual Boot) or, if your windows installation is old and getting slow:

1.- Re-install Windows first. When asked destination to install, choose make 1 partition and leave half hard disk unformatted.
2.- Install Xubuntu in the unformatted disk space.

---

### Post by Zickar on 2008-12-01
> **Dan_Dranath999 said:**
> If you install Xubuntu on your current partition (where Windows is) you'll delete windows.

Oh OK, So basically if Windows is on C:\ I should install Xubuntu on D:\ !! Does the installation ask me to setup a partition for installation ??

---

### Post by Dan_Dranath999 on 2008-12-01
If you have 2 hard disks (like me) it's gonna be easier. But Ubuntu "sees" the hard disks different than the way windows does:
It should see "hda", "hdb", "hdc", etc... (or sda, sdb, sdc)

You should verify how your LiveCD sees the windows disk, before attempting to install (it's not gonna see it as "C:/") just to be sure you are not installing Xubuntu on the wrong disk.

---

### Post by alain_sat on 2008-12-01
There is also a possibility to install it as one file on a Windows system.
During the installation process this will be asked.
I've done this on my Work Laptop as I don't have administrator rights and can't repartition the disk.

Another solution is during setup grub will let you resize existing partitions.

So if your Windows is still ok (that happens sometimes :) ) you can just realocate space during install.

After that you will have a dual boot system and be able to choose for Windows or Linux.

please try on forhand to check what partitions you allready have (rightmouse click on My Computer, manage storage) so you wont be afraid when Linux will speak about sda1 aso and not c: or d:

Good luck.

---

### Post by Zickar on 2008-12-02
thank you all for your help but I think i deleted windows, at the moment Xubuntu is running fine, internet and all is pretty functional but i can't seem to boot into Windows, I've never done this dual boot before except via a cd (without installing Xubuntu) so I just wanna know how can i be sure if I still have windows or not and how can I boot into windows because the system doesn't ask me what OS I want to boot into, it just starts Xubuntu automatically, any help is greatly appreciated

---

### Post by Malac on 2008-12-02
Sounds like you did delete Windows.
Open a terminal in Xubuntu and enter```
sudo fdisk -l
``` that's a lower case L not a digit 1. You will be asked for your passwd
Then cut and paste the output here.

This is mine:
   ```
Device    Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4111    33021576    c  W95 FAT32 (LBA)
/dev/sda2            4112        8222    33021607+   c  W95 FAT32 (LBA)
/dev/sda3            8223       10772    20482875   83  Linux
/dev/sda4           10773       30401   157669942+   5  Extended
/dev/sda5           10773       14883    33021576    6  FAT16
/dev/sda6           14884       15074     1534176   82  Linux swap / Solaris
/dev/sda7           15075       30401   123114096    7  HPFS/NTFS
```

---

### Post by Zickar on 2008-12-02
> **Malac said:**
> Sounds like you did delete Windows.
Open a terminal in Xubuntu and enter```
sudo fdisk -l
``` that's a lower case L not a digit 1. You will be asked for your passwd
Then cut and paste the output here.



```

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09ad09ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14596     3028252+   5  Extended
/dev/sda5           14220       14596     3028221   82  Linux swap / Solaris

```

---

### Post by Happypants on 2008-12-02
According to that you formatted the whole disk so you no longer have Windows on it anymore as it says your sda1 is now a Linux system.  

I don't know if Xubuntu has it built in, but Ubuntu comes with a program (albeit an older version) called Gparted that allows for easy partitioning.  It's pretty simple to use (hell... I figured it out).

You might look into that if you want to put Windows back on.

---

### Post by Zickar on 2008-12-02
> **Happypants said:**
> According to that you formatted the whole disk so you no longer have Windows on it anymore.


How could you tell and what should I do next time I install I install Xubuntu ?? What settings should I use ??

---

### Post by Happypants on 2008-12-02
> **Zickar said:**
> How could you tell and what should I do next time I install I install Xubuntu ?? What settings should I use ??

Check out my edit and it has the name of the program you should use.

Here's what it should look like if your disk still had Windows on it.
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5120    41126368+   7  HPFS/NTFS
/dev/sda3   *        5383       10604    41945715   83  Linux
/dev/sda4           10605       30401   159019402+   5  Extended
/dev/sda5           10605       29691   153316296   83  Linux
/dev/sda6           29692       30401     5703043+  82  Linux swap / Solaris

```

Notice how the first blocks (sda1) are NTFS and not Linux.  That's how I could tell. ;)

---

### Post by Tomatz on 2008-12-02
You need to set the **drive you installed xubuntu** on as **primary drive in the bios**. Then it will boot the linux bootloader (grub).

;)

---

### Post by Zickar on 2008-12-02
> **Happypants said:**
> According to that you formatted the whole disk so you no longer have Windows on it anymore as it says your sda1 is now a Linux system.  

I don't know if Xubuntu has it built in, but Ubuntu comes with a program (albeit an older version) called Gparted that allows for easy partitioning.  It's pretty simple to use (hell... I figured it out).

You might look into that if you want to put Windows back on.


But a Windows reinstall seems inevitable right ?? I'll just have to be careful for next time

---

### Post by Happypants on 2008-12-02
From what I can tell right now yes.  However... Is your entire Hard disk 120 gig like it says in your fdisk read out?

---

### Post by Zickar on 2008-12-02
> **Happypants said:**
> Check out my edit and it has the name of the program you should use.

Here's what it should look like if your disk still had Windows on it.
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5120    41126368+   7  HPFS/NTFS
/dev/sda3   *        5383       10604    41945715   83  Linux
/dev/sda4           10605       30401   159019402+   5  Extended
/dev/sda5           10605       29691   153316296   83  Linux
/dev/sda6           29692       30401     5703043+  82  Linux swap / Solaris

```

Notice how the first blocks (sda1) are NTFS and not Linux.  That's how I could tell. ;)


Thanks a load, I Just read your edit ... really appreciate it 
Ilooks like reinstalling windows it is and I'll probably be more careful next time, I Think I Might even try Ubuntu cause it seems to be easier and has a bigger community and thus better support I guess 

and yes my entire hard disk is 120

---

### Post by Zickar on 2008-12-02
so windows is as good as gone, I don't really care about Windows TBH Its just the files on it that I care about and I just wanna know if there is anyway I can acess the files that were on my Hard disk while using Windows on the C:\ and D:\ before I reinstall windows, I think this logically should be possible right ?? the Disks aren't reliant on the OS so I should be able to ascess their contents right ??

---

### Post by OrangeCrate on 2008-12-02
> **Zickar said:**
> How could you tell and what should I do next time I install I install Xubuntu ?? What settings should I use ??

IMO, futzing around with the partitions manually, is for mid to advanced users. For most of us, downloading, and using a Live CD for installation is the best option.

During installation, it'll walk you through the partitioning process. I've offered you a link below, for a tutorial on the Ubuntu install, and, it'll be similar if not the same for the Xubuntu Live CD.

If you have another operating system already installed, it will automatically give you the option to keep your existing OS, and install the new operating system in another partition.

The Live CD makes the installation process quite easy...

[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

---

### Post by Zickar on 2008-12-02
> **OrangeCrate said:**
> IMO, futzing around with the partitions manually, is for mid to advanced users. For most of us, downloading, and using a Live CD for installation is the best option.

During installation, it'll walk you through the partitioning process. I've offered you a link below, for a tutorial on the Ubuntu install, and, it'll be similar if not the same for the Xubuntu Live CD.

If you have another operating system already installed, it will automatically give you the option to keep your existing OS, and install the new operating system in another partition.

The Live CD makes the installation process quite easy...

[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

Aha, Thanks  lot, I think I chose the second option and hence my Windows was deleted 
Thanks a lot again for all the help

---

### Post by OrangeCrate on 2008-12-02
> **Zickar said:**
> Aha, Thanks  lot, I think I chose the second option and hence my Windows was deleted 
Thanks a lot again for all the help

You're welcome.

:)

---

### Post by Happypants on 2008-12-02
> **Zickar said:**
> so windows is as good as gone, I don't really care about Windows TBH Its just the files on it that I care about and I just wanna know if there is anyway I can acess the files that were on my Hard disk while using Windows on the C:\ and D:\ before I reinstall windows, I think this logically should be possible right ?? the Disks aren't reliant on the OS so I should be able to ascess their contents right ??

Glad I could help ya in any way I could.

Accessing the data on the disk after overwriting the OS; you're completely right, the data is still (mostly) there.  How do you get to it?  I haven't the slightest idea.  The data is actually still written on the hard disk, your OS has just been told to ignore it and write over it when it sees it.  Most of the stuff (unless you filled a ton of space immediately after install) is still physically on the disk, just not logically.  I'm sure that there are people out there who know how to retrieve it, but I'm going to guess that it won't be easy.  Let this be a lesson to you to back up data before you format a drive.  :p


Good luck in all your endeavors and I hope you enjoy Ubuntu as much as I have.

---

### Post by Zickar on 2008-12-02
> **Happypants said:**
> Glad I could help ya in any way I could.

Accessing the data on the disk after overwriting the OS; you're completely right, the data is still (mostly) there.  How do you get to it?  I haven't the slightest idea.  The data is actually still written on the hard disk, your OS has just been told to ignore it and write over it when it sees it.  Most of the stuff (unless you filled a ton of space immediately after install) is still physically on the disk, just not logically.  I'm sure that there are people out there who know how to retrieve it, but I'm going to guess that it won't be easy.  Let this be a lesson to you to back up data before you format a drive.  :p


Good luck in all your endeavors and I hope you enjoy Ubuntu as much as I have.


hehe, thanks a lot, well I spent all day trolling forums asking them all sorts of questions,the most helpful were the people here at Ubuntu and the people of Neowin mostly because it involves Ubuntu and Windows and I Think these two forums have the smartest people ... I have learned the importance of backing up though .... :D :D

---

