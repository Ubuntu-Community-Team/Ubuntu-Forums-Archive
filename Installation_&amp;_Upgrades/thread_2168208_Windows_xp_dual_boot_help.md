---
title: "Windows xp dual boot help"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by a1b2 on 2013-08-16
I tried doing a dual boot windows xp and ubuntu on 2 different hard  drives. I now have windows on c and ubuntu on "b"(?). The only way to  boot into ubuntu is to change hard drive boot order in bios.

How do I get the grub2 OS choice screen at boot up instead of changing bios settings.

---

### Post by Petro Dawg on 2013-08-16
If you already have your Ubuntu installed, you can try running Boot-Repair from a live CD session and it usually sets everything up for you rather nicely.

[This]("https://help.ubuntu.com/community/Boot-Repair") is useful documentation to help you through the process. I also dual boot across two hard drives with XP and Ubuntu12.04 and have used Boot-Repair successfully recently to correctly set up grub.

---

### Post by oldfred on 2013-08-17
You have to change BIOS to boot from Ubuntu drive before it boots from Windows drive.
You also may need to update grub menu.
sudo update-grub

Boot-Repair will fix many boot issues, but cannot change BIOS setting on which drive you boot from.

---

### Post by a1b2 on 2013-08-18
Thanks every one for trying to help me.   

 I ran boot repair and when I restarted I was completely locked out of  windows and Ubuntu now asked for a password and the one I created no  longer worked.

So now I have since used the windows disk to fixboot and fixmbr and got back  into windows in the "C"drive where I ran chkdsk find and repair. I have  also completely wiped my "D" drive of ubuntu and would like to start  over but Ubuntu cannot find windows to do a dual boot.

Ubuntu works so easy when installing in my test computer with 1 hard drive but not my regular PC with 2 hard drives. 

Very puzzling.

---

### Post by Petro Dawg on 2013-08-18
I only ever dual boot using 2 hard-drives (Ubuntu and XP), but it does require getting your BIOS settings and cable connections correct. Make sure your hard-drives have the proper jumpers selected if they require it (eg.  Cable Select on each).  Also make sure you have the drives connected to correct cables (assigned correctly).

Also be sure your BIOS has all the drives activated (Master 1 and Slave 1 or Master 2, ect...)

I typically have my Ubuntu drive set up as "sda" (drive 0 cable), and windows "sdb" (drive 1 cable).
 
Then install Ubuntu from live disk which should install grub to "sda" (ubuntu drive) as well (I like to leave the Windows drive alone as much as possible).  Then set bios to boot from "sda" first on re-boot.

---

### Post by oldfred on 2013-08-18
If you have two hard drives I prefer to have Windows on one drive and Ubuntu on the other. And configure so each totally works without the other. Some suggestion disconnecting hard drive which works well if willing to open computer.
You can do it just as you install but have to use Something Else or manual install and also on partitioning screen have to choose the Ubuntu drive as the location to install grub2's boot loader. Then if BIOS choose the Ubuntu drive to boot from.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)


 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If dual booting with Windows you may also  want a shared NTFS data partition for any data you may want from both systems.

---

### Post by a1b2 on 2013-08-18
Thank you Petro Dawg and oldfred.  This is what helped me  [http://askubuntu.com/questions/141656/ubuntu-12-04-installer-does-not-see-windows-already-installed-on-my-computer](http://askubuntu.com/questions/141656/ubuntu-12-04-installer-does-not-see-windows-already-installed-on-my-computer) 

This section in particular - 
------------------------------------------------------------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo os-prober

   The computer did not respond, so I entered

   ubuntu@ubuntu:~$ sudo apt-get -y remove dmraid

   to which the computer responded with

   Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dmraid
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 141 kB disk space will be freed.
(Reading database ... 147515 files and directories currently installed.)
Removing dmraid ...
update-initramfs is disabled since running on read-only media
Processing triggers for man-db ...

   I then entered

   ubuntu@ubuntu:~$ sudo os-prober

   and the computer responded with

   /dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Recovery Environment (loader):Windows1:chain
ubuntu@ubuntu:~$
   [HR][/HR]Replace the windows 7 stuff with windows  xp in the quote.   I am  now dual booting  Ubuntu and XP with the proper grub screen with OS  options.

Thanks again!

---

### Post by oldfred on 2013-08-19
Were drives ever RAID? May be better to remove RAID meta-data. I think you made it work just by removing dmraid, but the meta-data is still on drive. System may later reinstall dmraid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by a1b2 on 2013-08-19
Thanks again oldfred,

I did the   "sudo dmraid -ay" and sure enough it showed some RAID info on  SDA from the original install in 2009! I did have the motherboard based  RAID running when I first built this thing but it was such a pain in the  rear. Every BIOS update or major change in BIOS settings would require  you to re set all info in BIOS RAID or it would break the RAID and not  be able to rebuild.

Only option was complete wipe and reinstall, I did this at least 6 times between 2/2009 and 8/2009 when I stopped trying RAID.

"sudo dmraid -E -r /dev/sda"   Removed RAID data from SDA.

 "sudo dmraid -E -r /dev/sdb"   Nothing found.

 "Also check BIOS for raid settings" RAID is off in BIOS and has been for years.

I now back up to NAS with a hardware RAID card that never breaks.

---

