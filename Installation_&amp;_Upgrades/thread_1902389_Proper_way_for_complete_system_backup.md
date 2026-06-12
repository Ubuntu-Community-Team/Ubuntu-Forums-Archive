---
title: "Proper way for complete system backup"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2011-12-30
Folks,

In the past, I have backed up Windows partitions using Norton Ghost. I would appreciate your help in understanding proper way to completely backup Linux system.

Under Windows, I used to partition the disk in two partitions. C:\ drive would be for Windows files and D:\ drive would be designated for data files. I would then backup C:\ partition. In case of a problem, I just restore C:\ partition.

Things seem to be a bit different under Linux world. First, it appears you backup and restore from within Linux system itself as opposed to booting from an external CD and carrying the backup.

My first question is if backup/restore from within the OS itself is reliable enough. Won't I run into locked files issues? Also, can it happen that my system gets so toasted that I cannot even login into the system?

It appears one has to use "dd" to backup the partition. I am used to using Ubuntu's automatic partition method during install. In this case, which partitions must I backup? It has to be a "complete" backup so that the system can be restored to the exact same state.

Finally, is there a checkpoint backup mechanism under Linux/Ubuntu? Perhaps I could simply use this mechanism.

Any other advice would be appreciated.

Thank you in advance for your help.

Regards,
Peter

---

### Post by jerrrys on 2011-12-31
For Hdd or partition backup I like clonezilla.  Its simple and reliable and gives you a complete system backup.

[http://clonezilla.org/](http://clonezilla.org/)

For a daily backup of personal files I use rsync with a GUI called Lucky Backup and or grsync.  You have rsync already installed, its part of the default install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup&sa=Search&cof=FORID:9)

---

### Post by bluexrider on 2011-12-31
> **jerrrys said:**
> For Hdd or partition backup I like clonezilla.  Its simple and reliable and gives you a complete system backup.

[http://clonezilla.org/](http://clonezilla.org/)

For a daily backup of personal files I use rsync with a GUI called Lucky Backup and or grsync.  You have rsync already installed, its part of the default install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=backup&sa=Search&cof=FORID:9)

clonezilla is almost like Norton Ghost. It works well

---

### Post by sammiev on 2011-12-31
+1 for [Clonezilla]("http://clonezilla.org/"), I use it all the time to backup different OS all at the same time. :)

---

### Post by Mark Phelps on 2012-01-01
While I readily endorse using Clonezilla, one really IMPORTANT thing that you need to know, especially if you are familiar with Windows solutions like Ghost or Macrium Reflect ...

Is that with Clonezilla, you select the destination FIRST!

Yeah ... that can be really confusing, because with the Windows solutions, you generally select the SOURCE first.

Also, unless you really want to back up ALL the partitions on the drive every time you run Clonezilla, make sure you select the "saveparts" option -- which allows you to select individual "part"itions.

---

### Post by Lozzy_uk on 2012-01-01
> **Mark Phelps said:**
> with Clonezilla, you select the destination FIRST!

Thanks for that heads up - it's an important point


> **Mark Phelps said:**
> "saveparts" option -- which allows you to select individual "part"itions.

Am I right in thinking it does the entire partition, irrespective of data content?

---

### Post by bluexrider on 2012-01-01
**[COLOR=#3333ff]Limitations:[/COLOR]**

 
[LIST]
[*]The destination partition must be equal or larger than the source one.
[*]Differential/incremental backup is not implemented yet.
[*]Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.
[*]Software RAID/fake RAID/firmware RAID is not supported by default. It's can be done manually only.
[*]Due to the image format limitation, the image can not be  explored or mounted. You can _NOT_ recovery single file from the image.  However, you still have workaround to make it, read [this]("http://drbl.org/faq/fine-print.php?path=./2_System/43_read_ntfsimg_content.faq#43_read_ntfsimg_content.faq").
[*]Recovery Clonezilla live with multiple CDs or DVDs is not  implemented yet. Now all the files have to be in one CD or DVD if you  choose to create the recovery iso file.
[/LIST]

---

### Post by PeterTaps on 2012-01-01
Thank you all for your help. Looks like the verdict is to use clonezilla.

Regards,
Peter

---

### Post by bluexrider on 2012-01-02
> **PeterTaps said:**
> Thank you all for your help. Looks like the verdict is to use clonezilla.

Regards,
Peter
Please mark this 
(SOLVED)

---

