---
title: "grub rescue after install"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by jrhayden82 on 2015-01-13
Installed Ubuntu via live CD / net install, downloaded and installed ok. Had it use the whole hard drive. However after it restarted the computer it comes up with grub rescue. How can I fix this?

[[img=http://s9.postimg.org/et3dkisxn/IMG_20150112_221553_331.jpg]](http://postimg.org/image/et3dkisxn/)

---

### Post by fantab on 2015-01-13
Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool from Live Ubuntu, run '*create Bootinfo Summary*', note down the url link to the file and post the link back here. That will give us a detailed info.
You don't have to run any repairs yet with Boot-Repair.
Also post more info about your machine... cpu, memory, grapichs, etc.

---

### Post by jrhayden82 on 2015-01-14
[http://paste.ubuntu.com/9752355](http://paste.ubuntu.com/9752355)

System:
Processor: 2x AMD Athlon 64 X2 Dual Core 4400+ 2310.57MHz
Memory: 1791MB
250GB Hard Drive ( SATA )

---

### Post by oldfred on 2015-01-14
I do not see anything wrong.

Is BIOS set to AHCI, not IDE nor RAID?

A few older BIOS have issues with larger drives. For those the install of / needs to be fully inside the first 137GB of a drive and rest of drive can be /home or data.
You can have / (root) be just 25GB and rest of drive as /home, but have to use Something Else to install with the separate /home.

You can test to see if boot files beyond a ceratain point is the issue just by using gparted on live installer and shrink / to less than 100GB. Then you can reinstall or just move /home to a new partition you create for rest of drive.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by jrhayden82 on 2015-01-14
I tryed using the boot repair and it failed.

[http://paste.ubuntu.com/9752847](http://paste.ubuntu.com/9752847)

Am thinking about whiping the whole hard drive, and try re-installing Ubuntu. As the only thing on the hard drive is Ubuntu, and its not working due to the boot issue.

---

### Post by oldfred on 2015-01-14
Partition table shows partitions, but script was not able to mount any??
UUID could not then be seen either.

If reinstalling and not planning on Windows, I find the gpt partition table a bit more reliable. Ubuntu can boot from gpt with either BIOS or UEFI, where Windows only boots from gpt with UEFI.

You do have to have to have a 1 or 2MB unformatted partition with the bios_grub flag for grub to install correctly with gpt partitioning.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by jrhayden82 on 2015-01-14
Am running a disk whipe Dban. To whipe out everything on the computer, and will try installing Ubuntu after that. There should only be Ubuntu on the hard drive, as I am not a windows fan, and have been using Linux senice 2009, Which is when I bought this desktop. Have had Ubuntu, Linux Mint, CentOS, RedHat 9, and a few others on it. Haha kinda feel bad for the hard drive, after all I have done to it, yet it still works.

---

### Post by yancek on 2015-01-14
> Am running a disk whipe Dban

You don't need to do that, just select to format the partition(s) you plan to use during the install.

---

### Post by jrhayden82 on 2015-01-15
[http://paste.ubuntu.com/9759554/](http://paste.ubuntu.com/9759554/)

---

### Post by fantab on 2015-01-16
You have LVM... either remove it by reformatting the HDD or read [Here]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html") and [here]("http://www.tutonics.com/2012/12/lvm-guide-part-2-snapshots.html") to know more....

If you have no idea how you got LVM on HDD then reformat the HDD using Gparted.
Gparted -> Device -> create new partition table -> default=msdos ... this operation will delete all partition on HDD.
Recreate partitions with **ext4** (used as default by most distros) file system.... or let the default Ubuntu installer make 'em for you. Just don't select LVM setup.

---

