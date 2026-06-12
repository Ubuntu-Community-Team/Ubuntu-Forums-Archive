---
title: "Grub menu still missing after Boot-Repair (Lubuntu + Windows 10)"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by mcweb on 2016-02-16
See [http://paste.ubuntu.com/15097209/](http://paste.ubuntu.com/15097209/)


I used Gparted to move and shrink my Lubuntu partition so I could add a partition to install Windows 10. After that installation, my system booted directly into Windows, when I was hoping to see a Grub dual boot menu. After I ran Boot-Repair-Disk, the Grub menu was still missing.


I think Lubuntu is on sda2. I wonder if this message is relevant: Unknown BootLoader on sda2

---

### Post by zircon_34 on 2016-02-16
the best thing to do to my opinion, if you have to install linux in dual boot with windows, a) install windows first then b) install linux. Perhaps, there is a way to fix this, anyone? if you have no important files on the linux system, I would try to reinstall it including grub on the right partition (Ubuntu should recognize your windows partition automatically).

However, I do not want to recommend installing windows as to my opinion, linux is awesome, win10 is a compilation of spyware and potential viruses. I would contain that thing in a virtual machine such as virtual box (if you hardware is up to it).

---

### Post by zircon_34 on 2016-02-16
your partitioning also looks weird to me, your swap is on sda, linux is on sdb... 

how I do it, is to create a partition for linux e.g. your sdb, there I have the filesystem (ext4) mounted on "/", then I have swap mounted on swap, then I have my home folder partition (ext4) mounted on "/home". 

Perhaps this is of better help than I am [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by oldfred on 2016-02-17
Windows has a bug and does not write a logical Linux partition back to partition table.
It has done this since Windows 7.
You show a large number of sectors  starting from start of extended partition and start of swap partition.
      ```
 /dev/sda2         [COLOR=#ff0000]226,271,232[/COLOR]   488,396,799   262,125,568   5 Extended
/dev/sda5 [COLOR=#ff0000]        471,721,984[/COLOR]   488,396,799    16,674,816  82 Linux swap / Solaris


```    

Some say parted rescue is easier than testdisk.
       Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[URL="http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462"]http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462
[/URL]
 sudo parted /dev/sda unit s print
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)

[URL="http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462"]
[/URL]

---

### Post by mcweb on 2016-02-17
Thanks, oldfred. Parted rescue showed my Linux partition as unallocated :eek:, but I could see the missing files and folders with [testdisk]("http://http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") before it wrote the new partition tables. I still don't have the dual-boot option of GRUB, though I will try running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") again in a few minutes. At least now I can use [ext2explore]("https://sourceforge.net/projects/ext2read/files/Ext2read%20Version%202.2%20%28Latest%29/") to copy 8 years of work files to my Windows partition. I have been running Windows in Virtualbox, but my supervisor asked me to switch to Windows host/Linux guest.

Here's the working link on [How-to Fix Invalid MSDOS Partition Tables]("http://gparted.org/h2-fix-msdos-pt.php") with GParted.
[h=1][/h]

---

