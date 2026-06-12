---
title: "Installing Ubuntu 12.04 to own drive"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by loybanks on 2013-05-17
I'm wanting to install Ubuntu 12.04 to the second drive or M:

Windows 7 is already on C:

I've set up to install to /boot

Will this produce a boot menu? If not, what must I do to get a boot menu?

All suggestions are always appreciated.

---

### Post by oldfred on 2013-05-17
Just to be sure is M: a separate drive not just a partition. Windows uses the term drive for both partitions and physical drives. Linux uses sda, sdb etc for phyiscal drives and the numbers like sda1, sda2 for partitions on the drives. Often users over write their entire Windows installs because they did not realize the difference.

If you installed and used manual install so you could specify to install the grub2 boot loader to the second drive's MBR then you have to change BIOS to boot from the second drive. Anything else defaults to install grub to sda and it is better to keep the Windows boot loader in the MBR of the Windows drive. (Different for UEFI).

Post this:
sudo parted -l

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer not available with newest versions of Ubuntu. But install process the same with gui installer.
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by loybanks on 2013-05-17
Thanks for the fast reply. Windows is installed on sda, no partitions there. My plan is to install Ubuntu on M:, (sdb) a separate drive that will have two partitions. I'm having the drive split into two partitions. Should I not do this? Would I be better to have installed on complete drive? What might be the reason? I'll hold up on this until I hear from you. Thanks.

---

### Post by fantab on 2013-05-17
Partitions on a Hard Disk can be analogous to Rooms in a House. Its your choice depending on your need. If you think only one partition/room is enough then its enough. Its a very personal thing. However, Ubuntu needs at least two partitions one for "/", to house your system files and data and SWAP partition. 

What do I do? I will split my 'system files' and 'my DATA' into two different partitions. Why? If ever there were a system crash or for any reason my system becomes unbootable, there is risk of loosing all my data. Offcourse there are recovery tools, but no recovery tool guarantees you 100% recovery. Why would I want to take that risk with my precious data. This also applies to Windows or any other OS. I dual boot with Windows on one of my machine (though I haven't used Windows in a while now). I have two hard disks. Windows on one and Ubuntu on another and this is how my partitions look:

Windows: /dev/sda
/dev/sda1 (or Winodws C about 70GB NTFS
/dev/sda2 (or D 50GB NTFS (I use this to Download stuff directly to)
/dev/sda3 (or E All the remaining GB NTFS (to store my DATA, also used to share DATA between Windows and Ubuntu)

UBUNTU: /dev/sdb
/dev/sdb1 25GB Ubuntu "/" Ext4 (for system files)
/dev/sdb2 25GB Free Partition Ext4 (in case I want to install another Ubuntu version or flavor or another distro)
/dev/sdb3 4GB SWAP
/dev/sdb4 All the remaining GB Ext4 (for my Linux only DATA) or /home

I have installed Ubuntu bootloader, GRUB on /dev/sdb (if you don't tell instaler where to install GRUB it will be installed to /dev/sda, and overwrite windows boot files from MBR). When I install Grub on /dev/sdb, Ubuntu own disk then my Windows is not disturbed.

By default BIOS will boot /dev/sda first. So only Windows, no Ubuntu. What do I do? I change the HDD boot order from BIOS to load /dev/sdb first. Ubuntu_GRUB will boot now and present me a menu to either boot Ubuntu or Windows. Windows bootloader, on its own cannot boot Ubuntu but Grub can boot both Ubuntu and Windows and many more.

my two cents...

---

### Post by loybanks on 2013-05-18
Thanks for the comprehensive reply. What you've said goes right along with the info in the links sent to me by oldfred. I really do appreciate the information from all. I will follow your suggestion and install that way. So far I haven't done anything other than clean up the drive, reformat, etc. Later today I'll get on it.

For the record I'm a 73 year old codger in southern Colorado. What I do is experiment with computer projects, such as this. Keeps my fingers and mind active. Then I go out and tend to my roses and trees. Just thought you guys might like to have this very valuable info on me. :) Thanks again. If I run into any issues I'll get back to you.

---

