---
title: "Recuperate Ubuntu partition"
date: 2018-01-13
forum: Installation &amp; Upgrades
---

### Post by averyaab on 2018-01-13
My Asus laptop has both windows 10 and Ubuntu. After the last windows update it erased my grub and couldn`t Access any system, only rescue grub.
I fixed it with Windows grub but now doesnt recgnize my Ubuntu partition.
Now booted an Ubuntu ISO and accessed the try Ubuntu without installing.
I cannot find my Ubuntu partition from “fdisk -l”
Here is a picture where you can see “GParted” and I believe the partition I want to recuperate is the one underlined, that says “unallocaed”. 

[IMG]http://es.tinypic.com/r/6profa/9[/IMG][IMG]http://i67.tinypic.com/6profa.jpg[/IMG]

---

### Post by yancek on 2018-01-13
The fdisk output shows that your Ubuntu partition is still there based on the start/end sectors for the Extended and swap partitions.  This happens with some windows updates which rewrite the partition table and exclude non-windows partitions.  I'm not sure how to resolve this so just search for how to recover linux partition after windows upgrade here at the forums or online while waiting for a reply from someone more knowledgeable on the subject.

---

### Post by oldfred on 2018-01-13
This has been a bug in Windows updates or installs for years. It just does not recognize valid logical Linux partitions.

Parted rescue or testdisk are the two ways to recovery partition. You may have to reinstall grub.
If one partition and since you know approx beginning & end, parted rescue may be slightly easier. If more than one partition then try testdisk.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 


 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 


These are all essentially the same, some parted rescue, some testdisk. Read several as some explain process better.

 [SOLVED] Windows 10 update, Stuck in grub rescue 
[https://ubuntuforums.org/showthread.php?t=2373061](https://ubuntuforums.org/showthread.php?t=2373061)
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

