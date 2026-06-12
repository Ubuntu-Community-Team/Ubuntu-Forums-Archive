---
title: "Installing new hard drive."
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by blackbird3216 on 2011-07-22
I made a post earlier this month about installing a secondary hard drive, so that I can finally create backups. I solved the problem of not having enough screws by simply "borrowing" some screws from the computer case (the screws I took simply lock the sliding sides, but they are not really necessary). 

Now, I boot up my BIOS, and unfortunately, it seems I plugged in the HD into SATA 5. 

SATA 0 is my main hard drive. SATA 1 is my DVD drive. SATA3 and 4 don't exist (for some odd reason) and SATA 5 is the second hard drive. I see that BIOS recognizes it, but Ubuntu does not. Then, I opened Gparted, and I see that the HD is "unallocated." Do I need to allocate it before Ubuntu is cognizant of the HD? 

My ultimate goal is to have this HD installed, then backup my documents/pictures/music temporarily onto the second drive. Finally, I will install Ubuntu 10.04 LTS, since its my work computer. 

I considered installing 11.04, but considering that support for 11.04 is shorter than for the LTS, and adding to the fact that Unity is very controversial for not being polished enough, I feel that the LTS would be the best solution.  

Another question I had was regarding automatic backup programs. I remember that a someone here pointed me toward "clonezilla" but I don't know how such programs work. I would ideally prefer something that makes hourly backups, but does not have to recopy the entire file, only the changes (kind of like Apple's Time Machine). I would also like something with a GUI.

---

### Post by e79 on 2011-07-22
> Then, I opened Gparted, and I see that the HD is "unallocated." Do I need to allocate it before Ubuntu is cognizant of the HDI'd say yes to that one, a bit like 'initializing' a disk in Windows prior to format it. Here's some documentation from Ubuntu to use Gparted  [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive).

> My ultimate goal is to have this HD installed, then backup my  documents/pictures/music temporarily onto the second drive. Finally, I  will install Ubuntu 10.04 LTS, since its my work computer. Wise decisions :D

> Another question I had was regarding automatic backup programs. I  remember that a someone here pointed me toward "clonezilla" but I don't  know how such programs work. I would ideally prefer something that makes  hourly backups, but does not have to recopy the entire file, only the  changes (kind of like Apple's Time Machine). I would also like something  with a GUI.     Rsync would do that for you :P, check in the Ubuntu Software Center for somethng called _**LuckyBackup**_ or **_Grsync_**; both use the power of Rsync in the background with a simple interface

Hope this helps

---

### Post by -kg- on 2011-07-22
With regard to GParted showing the hard drive "Unallocated", what Gparted is showing is your disk.  Since it is brand new, it has no partition, and hence Ubuntu will not "see" it.  You will need to create (a) new partition(s) on it and format them to the format you desire.

If you're going to access the drive from Windows as well as Linux, you will want to format it to NTFS.  If just from Linux, you can format it to ext3/4, as you desire.

For more information on partitioning operations, read at the link in my signature block.

---

### Post by blackbird3216 on 2011-07-22
Hmm. I created an ext3 partition using the default settings in Gparted, and now ubuntu recognizes it. However, I cannot copy any of my files to it. I remember the first time I mounted it, it requested my password. when I right click, the "paste" option is grayed out.

---

### Post by blackbird3216 on 2011-07-22
I was able to figure it out. First, I need to get into fstab and change the mounting point to mount automatically. 

Then, I had to change permission through terminal. 

Now, I'm copying my files over. 

When I do the fresh install, probably later tonight, will I need to repeat this process (going into fstab) or will the installer automatically do that?

I will take a look at the backup utilities later, since I am trying to run the fresh install first.

---

### Post by e79 on 2011-07-22
You would have to use the fstab to recreate the entry as you just did, as I would choose the safe side and don't ask Ubuntu to touch this 'backup partition for now' if you want to avoid any chances to lose files.

---

