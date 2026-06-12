---
title: "Grub Rescue - cant boot anything"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by liam4 on 2013-10-06
I tried to install Ubuntu 13.04 alongside Windows 7 on my HP laptop today. All was well, until I rebooted and was greeted with a command line called grub rescue, saying no such device. I know this issue has been posted before, but none of their answers have helped. I know that the install was going to be interesting, as my laptop has two hard drives, a 32GB SSD called the 'OS', and I think its running Intel's RAID. Then the other harddrive is for personal stuff. 
I was able to run the live usb again and follow some tutorials to reinstall grub, and run the boot-fixer program with apparent success, untill I reboot and found myself in the grub rescue command line. Ive also tried to run a windows recovery disk, but it doesnt work (Gets stuck on "Start Boot from usb")
 One more thing, I noticed that the partitons are seperated like so... 
dev/sda     (i think) Windows 
-sda1
-sda2
and 
dev/sdb    (i think) Ubuntu
-sdb1          This one I think is the problem, as it says its a 'OS/2' Hidden C: Storage
-...
-sdb5     This one (i think) is the main Ubuntu Drive
To sum up, basicly is there a thing I may have missed or something I havent tried yet that may get (at least) Windows going again and (if Im lucky) Ubuntu.
I dont have anything important on the Linux Partition.
Thanks heaps for your help, 
Liam

---

### Post by oldfred on 2013-10-06
Your sdb, the SSD is not really OS/2 partition type, but is the Intel SRT which somehow uses RAID that causes grub to not install. Desktop installer does not support RAID (you need server for RAID). Most turn off the Intel SRT in Windows and remove the RAID meta-data since you really have a desktop. Then you can reimplement the Intel SRT and it will readd the meta-data and work.
Some that want Ubuntu more than faster Windows, just install Ubuntu / (root) to the SSD and never turn on the Intel SRT. Others just install Ubuntu to hard drive. Some with larger SSD have been able to sqeeze a small Ubuntu into part of the SSD and still have the Intel SRT as it does not seem to use all of SSD?

Brand of computer does not make much difference. It is Windows & Intel SRT.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by liam4 on 2013-10-06
Thanks, so all I have to do, is install ubuntu after ive disabled raid on my SSD. Will reinstalling Ubuntu fix grub?

---

### Post by oldfred on 2013-10-07
You can remove RAID meta-data and run Boot-Repair to install grub.  Or you can re-install.
I think Ubuntu installs correctly it just is grub that does not know where to install. It should be in MBR, but with RAID it normally goes into the RAID not MBR. But your RAID is not standard RAID.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by nathanservicesinc2 on 2013-10-07
Theres going to be a whole bunch of other packages to download after you finish the download of Ubuntu 13.04 ; you'd better do them real quick when you first get internet access or else.

---

### Post by nathanservicesinc2 on 2013-10-07
The Grub should show you a list of commands that it will accept; start going thru the list once you get there.

---

### Post by liam4 on 2013-10-07
Sweet thanks guys :)

---

