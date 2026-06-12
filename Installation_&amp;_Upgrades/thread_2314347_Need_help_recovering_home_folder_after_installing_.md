---
title: "Need help recovering /home folder after installing Windows 7"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by joe196 on 2016-02-20
Hello, I am a newbie here and this is my first post.

I know that this topic has been posted before and I followed them but I am stuck in the procedure, that is why I am making another post to get some help.

I had an existing Ubuntu installation with two partitions: one for root and another for home. I didn't install a swap partition because I am using SSD.
I needed to re-install Windows 7 as well. So I did, and installed 7 after Ubuntu in a different partition. After installation, I had to fix the boot, so I put my ubuntu live cd and ran a boot-repair. Now both OS are there, but my /home ubuntu partition is gone. Not only that, but gparted is showing that partition as unallocated (!).

I panicked, but did a lot of research and I found some useful posts here that showed me that I needed to use Testdisk. 
Never used Testdisk before but someone in here wrote that is my friend :) so I did a quick analyze and I can see my home partition in there. 

Here is the result:

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
   HPFS - NTFS              0  32 33   191  89 26    3072000 [SYSTEM_DRV]
   HPFS - NTFS            191  89 27 20447 222 63  325421056 [7]
   HPFS - NTFS          20448   0 33 24991  85 54   72988672
>  Linux                20448  33  2 33202 214 36  204904448 [new_home]
   Linux                33202 247  6 41118 247 25  127170560
   HPFS - NTFS          41119 154 60 59016 144  8  287514624 [PROJECTS]
   HPFS - NTFS          59016 144  9 60801  80 15   28672000 [Lenovo_Recovery]
```

This [new_home] is the partition that I am looking for. The one right below is my root.

Why I am writing here is because I don't know how to move on from here. 
I pressed P and see that my files seem to be there, but when pressing ENTER to continue it says "No partition found or selected for recovery".

I saw many youtube videos but they all seem to move forward when pressing ENTER and their partitions can be mounted.
What should I do here in order to get this partition back to life?

Any help would be immensely appreciated.

---

### Post by joe196 on 2016-02-20
I did move forward a bit because I need to solve this soon. I chose the right and left keys and marked this partition [new_home] as logical (that is what the guide of Testdisk step by step is doing)
but then I had the grub error and so I marked my root partition as logical as well.

As a result.. I still dont have a /home folder.

And gparted is showing me this so basically everything is now unallocated, including windows folders.
:confused:

 [IMG]http://i.imgur.com/QZoK2B1.png[/IMG]

---

### Post by oldfred on 2016-02-20
It looks like you just restored the one partition that is /home, but did not include all your existing partitions.
Windows installs & major updates have for years had a bug where they do not write Linux logical partitions back into partition table.
Normally you add that missing partition back with testdisk or use parted rescue.
My main complaint is testdisk uses the old (very old) CHS way to show the drive. That has not been used for years. Drives use sectors and large block allocation.
 Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

      
 sudo parted /dev/sda unit s print
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

