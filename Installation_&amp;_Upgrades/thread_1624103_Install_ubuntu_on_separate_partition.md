---
title: "Install ubuntu on separate partition"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Fudgcicle on 2010-11-17
Hello, I am rather new to Linux but have been running it off of a flash drive in persistent mode for a couple of weeks now. Obviously this is not the most ideal way to run Linux and so I think I am just about ready to install Ubuntu to dual boot on my laptop alongside of Windows 7. I don't feel comfortable allowing the installer to automatically set the partitions so I am ( as of right now ) planning on using the built in partition editor on windows 7 to re-size my hard drive and install Linux on the new partition. I have a Sony Vaio with 4gb of ram and a 64 bit processor. So my questions are: is there any certain file system I should format the partition as? I am planning on giving Ubuntu around 30gb of space overall, will that be sufficient? Will I need to manually set all the partitions for Linux during the installation or can I tell it to use the whole disc and just point it towards the new partition? How much space should I give to swap? Will I have to do anything with Grub for it to boot?

---

### Post by sikander3786 on 2010-11-17
Hi. Welcome to the forums :-)

Yes 30GB would be sufficient. Actually Ubuntu will not need whole of that ever :) unless you save personal data to the same drive.

Use the Windows 7 partitioning tool to resize C: drive. Then run chkdsk on that drive before trying to install Ubuntu. Some recommend that you run chkdsk 3 times.

Don't format the freed up space to any file system. Leave it unallocated and re-partition it using the partitioner in Ubutnu installer.

Choose Manual partitioning on Installer's partitioning page. You'll need 2 partitions at least.

1. / partition. File system Ext4, Mount Point = /, Recommended Size = > 8 GB.

2. Swap partition. Size = RAM X 2.

Don't do anything to Grub. Let it install to its default location and it should pick up Windows for dual boot.

---

### Post by ajgreeny on 2010-11-17
How is your disk partitioned at the moment, as you can only have 4 primary partitions on a disk.  If you already have that many you will not be able to add more and will need to think hard about which to remove.

I think Win7 is often installed with extra partitions; one for boot, a second for restoration of the OS, a third as the OS itself, and finally another for data.  If that is the case you have a problem.

To help solve this boot to your flash drive install, run **System ->Administration ->gparted** and show us a screenshot of what it finds, and/or run ```
sudo fdisk -l
``` in terminal and report back the output from that.

---

### Post by Fudgcicle on 2010-11-17
Thank you for the help, I'm unable to take a screen shot of gparted  because I am out of disk space on my persistent drive and no matter what  I do I can't seem to free any up and it also wont let me save it to the hard drive... The output from the terminal is 

```
Disk /dev/sda: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7872     2015216    b  W95 FAT32

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2eb41af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1032     8287232   27  Unknown
/dev/sdb2   *        1032        1045      102400    7  HPFS/NTFS
/dev/sdb3            1045       38914   304179544    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```I  checked on the Windows partition tool also and it showed a recovery  partition, C:, and one more partition. So I'm assuming then that that  means I have three partitions on my drive already. Can I use a logical  partition for Ubuntu? Also, do I not need to specify /root and /home  partitions?

---

### Post by oldfred on 2010-11-17
I think everyone will give you slightly different advice on partitioning and none of them are wrong. Many things depend on how you use system and plan to upgrade in the future. I used just root & swap for about 3 years, but added a shared NTFS for any data I wanted between windows & Ubuntu.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Swap needs to be equal to RAM if you want to hibernate, but if not and you have more than 2GB you will rarely if ever use swap. If less than 512MB of RAM then you should have 2X RAM.

---

### Post by ajgreeny on 2010-11-17
As you have 3 partitions already, I suggest you shrink sdb3 with the windows own disk management application.  I have no idea what windows will call it, (D: C:?), but will be the largest partition on the disk.

Leave the space unformatted and then when you install, choose manual partitioning and make an extended partition of the whole free space, and then make three logical partitions in that, as suggested by oldfred, /(root), swap, and /home.

---

### Post by Fudgcicle on 2010-11-17
Ok. I think I'm pretty clear on what to do now. But does it matter if I use ext3 or ext4? What's the difference?

---

### Post by oldfred on 2010-11-17
You can use either.

Ext3 was the standard upgrade from ext2 that added journelizing. Ext4 added much higher speed, but early versions had some reliability issues. In fixing the issues it became only a little faster for most things. The main thing I notice is on every 30 boots it does a file check and with ext4 it is very quick where ext3 took forever. Ext4 is now the standard for default installs of Ubuntu, so there are not any remaining issues (or none more than any other software):).

---

### Post by Fudgcicle on 2010-11-18
Ok, so if I make all the partitions ext4 then obviously linux will be able to access every partition on my drive since it reads NTFS, correct? But will I be able to access files on my linux partition from windows? If not, can I set Linux up to save whatever files I download or put on my laptop to the windows partition?

---

### Post by oldfred on 2010-11-19
I suggest a shared NTFS partition. I do not like to write into the windows partition from Linux. Sometimes windows is not happy if too much change happens that it does not know about. Plus with Linux you have total access to everything in windows and can delete or modify the system that windows normally protects you from. I only write into windows to make repairs.

I created a shared NTFS partition and have had no issues with my windows XP install. I have Filefox & Thunderbird profiles in the shared partition, so which ever I boot have the same bookmarks and email.

---

### Post by Fudgcicle on 2010-11-19
Ok, I have made the unallocated partition and am trying to run chkdsk on it but I don't seem to be able to... I can only run it on the other three partitions. How do I run it on an unallocated partition?

---

### Post by oldfred on 2010-11-19
Chkdsk is a windows tool to repair NTFS partitions. Unallocated is not really a partition until you create it and then format it.

The unallocated you want to make into an extended partition using gparted. Then you can add many logical partitions for Ubuntu, swap & data.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Fudgcicle on 2010-11-19
Oh ok. I thought someone said to run chkdsk on the unallocated partition but now I think they just meant the C: drive. Just one more question now, how possible is it that I could mess up my hard drive installing linux? Is it likely that I will be unable to boot into windows? I'm a little bit paranoid about this happening... Thank you for all of your help.

---

### Post by oldfred on 2010-11-19
Anything is possible. That is why we suggest good backups.

The issue is more we make mistakes, we click on use entire hard drive when we did not mean to and erase the entire thing. Review these guides and do not select anything that says to use entire drive or entire partition. 

It is not difficult to reinstall the windows boot loader if necessary. But you need to then have a windows repair CD and/or a Ubuntu liveCD (or other linux liveCD) to make repairs.

So you can see what the sceens look like in advance, review these.
Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

If you have to reinstall a boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Fudgcicle on 2010-11-19
Ok. I am reading through those links. Thank you so much for all of your help!

---

### Post by Fudgcicle on 2010-11-19
I am starting through the process now, do I select beginning or end for the location of the new partition?

---

### Post by Fudgcicle on 2010-11-19
Ok... I tried to make a primary partition of the whole free space but then I can't add logical partitions. Do I just make 3 logical partitions out of the unallocated space? Or do I need the Primary?

---

### Post by ajgreeny on 2010-11-19
You make an extended partition in the whole of the unallocated area, not another primary.  After that, you can add logical partitions to the new extended partition as I suggest below.

I suggest you put the / (root) partition at the beginning of the unallocated area, 10GB;  swap at the end of the now reduced unallocated area, 4GB, or 2 GB if you will never hibernate;  and use all the rest for /home, so put that at the beginning of the second time reduced area, leaving no space before or after.

---

### Post by Fudgcicle on 2010-11-19
Well, it seems I'm all set ;). everything went fine and I'm now dual booting Ubuntu and windows 7. Thank you guys for your help.

---

