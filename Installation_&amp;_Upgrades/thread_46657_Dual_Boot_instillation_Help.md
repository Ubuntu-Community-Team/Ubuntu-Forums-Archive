---
title: "Dual Boot instillation Help"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by Infatuated_iPod on 2005-07-05
Hey, is there any way to install ubntu along side windows without haveing to reinstal windowns and re-partition the hard drive. At this point my laptop only has one partition and that is what windows is on. I would like to install ubuntu again. I heard of a program called partition magic, or something, but that is expensive. Is there any cheap and easy way to do it, or do i have to start from square one. 

Thanks! 

-Lev

---

### Post by frodon on 2005-07-05
The partition tool of the ubuntu install CD allow you to make partition with your free space in order to install ubuntu. You can make a partition with your free space and install ubuntu on it then when ubuntu is running use Gparted to resize your linux partition and make one more partition in FAT32 for window and ubuntu : [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php).

As far asi know partition magic is the only tool which allow to make partition with windows.

---

### Post by Darkscot on 2005-07-06
[QUOTE=Infatuated_iPod]Hey, is there any way to install ubntu along side windows without haveing to reinstal windowns and re-partition the hard drive. At this point my laptop only has one partition and that is what windows is on. I would like to install ubuntu again. I heard of a program called partition magic, or something, but that is expensive. Is there any cheap and easy way to do it, or do i have to start from square one. 

Thanks! 

-Lev[/QUOTE]

If you do a search on Amazon or even Ebay you can get Partition Magic for US$25 or less.  Look for the PowerQuest packaged version as it is usually cheaper than the new Norton version.  The software is identical it is just the packaing has changed since Norton bought it.  I think PM is a fantastic piece of software and well worth the money.  It has solved a lot of problems and makes all aspects of partitioning easy as pie.

---

### Post by sigma2805 on 2005-07-06
Hi. Do you have windows XP? if so you can use qtparted to resize your NTFS partition. it is an open source alternative to partition magic. to use it you need to download [System Rescue CD](http://www.sysresccd.org/download.en.php) which is a live cd. 

the first step is to run scandisk and then defrag your hard drive. to run scan disk go to my computer and then right click on the c:\ drive. choose properties. choose tools then error checking. check both boxes and push start. a dialog box will pop up telling you to run the check at bootup. choose yes and restart your computer. the scan disk will run automatically the next time windows starts up. Depending on the size of your hard drive and the amount of files you have this might take some time. once it has completed boot into windows and run disk defragmenter.

once that has completed put the system rescue cd into your cd drive and then reboot your computer. Your bios must be able to boot from a CD for the live cd to work. If it doesn't do it automatically you might have to enter the bios and change the boot order. you will know if your bios automatically boots to a cd because the system rescue cd will load. at the boot prompt i like to enter fb800 and then hit enter. This forces linux to display everything in 800x600 resolution. once everything has finished loading you must make a backup of your partition. to do that you need to first mount your floppy drive. to do so in the command prompt type 

mount -t ntfs /dev/fd0 /mnt/floppy

once that is done type 

sfdisk -d /dev/hda > bak-hda

now you need to copy the file over to the floppy drive. to do that you can run midnight commander. type "mc" (without quotes) at the command prompt again.  using this graphical interface go to the folder where bak-hda is. then copy it to /mnt/floppy.

now you are ready to run qtparted. at the command prompt type run_qtparted. choose your mouse. (make sure you turn on num lock to use the number pad)

once you are in qtparted choose the hard drive you want to resize from the left column. once it loads right click on the hard drive and choose resize in the main window. then choose how big you want to make the drive. it should now show you your primary windows drive and it should the amount of free space seperatly. once the process has completed go to file->commit.  this will write the changes. once this has completed you can exit the live cd by hitting ctrl-alt-delete. this will begin the shut down process. once this is complete make sure you remove the system rescue cd on reboot. then you can enter the ubuntu install cd and choose automatic partitioning and your all set. I'm also going to type this up with pictures to put it into the wiki today or tommorow if you want to wait. hopefully my instructions help you.

---

### Post by sigma2805 on 2005-07-06
also...its always good to make a backup of all the files you need or files that are important to you incase something goes wrong.

---

### Post by sigma2805 on 2005-07-06
you can also do it through the ubuntu installer if you choose to manually edit the partition table. Select the windows partition go to size and enter the size you want to resize that partition to. i prefer the graphical interface of qtparted though. plus you can make a backup of the partition using sfdisk with the system restore cd.

---

### Post by frodon on 2005-07-06
[QUOTE=sigma2805] i prefer the graphical interface of qtparted though. [/QUOTE]

Qparted is for KDE and Gparted for GNOME (it's the same software).
I think i will be easier for him to use the install CD even if qparted or gparted do the job really well with a user-friendly graphical interface.

---

