---
title: "Dual Boot Win 7 64 bits and Ubuntu"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by andrew122 on 2013-01-31
Hi all, 

This kinda questions is already being asked millions of times. But as a human being everyone thinks his/her case is different and I am no exception; Let me explain.

I am fairly new to Linux. I have an year old HP-dv6 laptop having Windows 7 64 bit. I want to dual boot it with Ubuntu. I have read many posts which has done nothing but confuse me more. 

I have few basic questions which might be childish..
(1) Do I actually need to create /, /boot, /root, /Home, /usr - these many partitions..?
I am going to use it single handed, without creating more than two accounts. 
(2) What is boot partition, How to write bootloader on it ? and if I am to write bootloader to /boot (i guess this is boot partition), how can I write bootloader to MBR also..?
(3) I am planning to wipe entire hard-disk because my Win7 is not managed neatly, almost all posts suggest that I should use Ubuntu after Windows 7. In that case, how to boot into Windows..? I have read about chainloader + 1 command but there are posts in which this has failed.
(4)I am planning to do partitions like this.

------------------------------------------------------------------------------------------
  Win 7   |  Ubuntu   |.............................................                                                   |8GB..|100MB
   20GB   |   20GB    ...| ......all NTFS data...............|SWAP|Win7
   NTFS   |   ext3     .....|                                                   ..............................................|........          |
------------------------------------------------------------------------------------------

But is it that Ubuntu 20GB is going to have /boot..? I want to go ahead with grub2.
(5) I have read that swap partition should be double the RAM size - but my RAM is 6GB, so giving 12GB is not fair.. maybe 8GB would be enough.


So guys please help me.. in as much detail as possible. Would love to see step by step guide - like do this, do this, do this..

Thanks in Advanced
Andrew

---

### Post by oldfred on 2013-01-31
Windows has to be installed to a primary NTFS partition with the boot flag. Windows 7 normally installs to two primary partitions the first the hidden 100MB boot/repair partition which has boot flag. I would make Windows a bit larger, some suggestions I have seen were 30GB as a minimum. NTFS partitions like lots of free space to work well. If you create the two partitions in advance Windows should just install to those two. If a blank drive Windows will just use entire drive and then you need to use Windows disk management to shrink the Windows partition.

You do not need all the Linux system folders as separate partitions. Often servers with unique requirements may need them. Only a few systems need a separate /boot, but if using a smaller 25GB / (root) partition near the beginning of the drive it should not be required.
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    
Swap needs to be the size of RAM in GiB (not GB) only if you want to hibernate. I have 4GB and do not think I have used swap ever. If you always load every app and edit videos then you may need swap with a newer system. But a small 2GB swap is still suggested, but some have none.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
   
All BIOS/MBR computers boot from the MBR. BIOS loads code in MBR that then looks for more code on drive as MBR is tiny. Either Windows or Grub has a boot loader in the MBR. Grub is designed to multi-boot but Windows is not. The rest of grub and the kernels are in the /boot folder and do not need to be a partition.

If you are using a separate NTFS data partition then you do not need a separate /home but will want to change a few settings to save most data into your data partition. When you get there more details here.
       Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

Some guides with screen shots.
Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

