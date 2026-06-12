---
title: "how to install Ubuntu in separate disk partition?"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by utsav_ubuntoo on 2012-07-30
Hello,
       I am totally new with the Ubuntu.I have windows xp installed in C drive.I am wandering to install ubuntu in D drive with dual boot option while booting my PC.Is it possible?kindly give me solution.... Regards....

---

### Post by darkod on 2012-07-30
C drive and D drive as windows calls them don't give enough information. They can be partitions on the same disk, or two different disks.

Ubuntu doesn't install on ntfs partitions so in any case it will not be able to install on the D partition. You will need to shrink some of the ntfs partitions first so that you can create unallocated, unpartitioned space on the disk.

only after that is done and you have confirmed XP is booting fine after the shrink, you can start installing ubuntu. If you don't want to use the manual install option it will install itself into the unallocated space you left.

As for shrinking XP, it doesn't contain a tool for that like vista and 7. You will have to use a third-party program or use the ubuntu cd in live mode and Gparted, to shrink one of the ntfs partitions.

---

### Post by leosubhadeep on 2012-07-30
You bet you can. :KS
**But make sure you do want to "install" Ubuntu** because you can use a "live distro" running from a removable media (e.g. CD/DVD, pen drive etc.). [Get more info about how to try Ubuntu before you install from here]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install").

To install, all you need are as follows:
[LIST]
[*]A bootable DVD/Pen drive containing the Ubuntu distro (get it from [here]("http://www.ubuntu.com/download") )
[*]At least 5 GB disk space on your hard disk. (For optimum performance)
[/LIST]To start installing, 
1. Start your system and go inside the BIOS (by pressing F2 as immediately the system starts). 
2. Change your boot device preference. Make DVD-ROM or bootable pendrive as first boot device. Save and exit by pressing F10. 
3. The system, with the bootable media inserted, restarts with an installation screen. Choose "Install.." from there. Follow the steps, keeping it mind that **_you don't want to replace your XP with Ubuntu but want to run along with it_** (dual boot). 
4. A cool partition manager will give you every flexibility to make you install Ubuntu in your desired disk space. 
5. On the free space, you have got to make at least one "root" partition (filesystem:ext4) and optionally but recommended a swap area (swap is same as "Virtual memory" used in Windows). Leave your XP partition as-it-is, create partition(s) on the blank space. (Do a bit google before using the partition manger if you're not sure)
6.On next step, you'll be asked where the MBR (Master Boot Record) should be created. Follow the steps accordingly. 
7. After installation is complete, remove the bootable media, restart, enter BIOS, change first boot device to be your Hard Disk (optional step), press F10. You're on!
 
**[COLOR=red]CAUTION: PRIOR TO DO THE ABOVE THINGS, LEARN MORE ABOUT IT, BACKUP YOUR IMPORTANT DATA, AND DO THE INSTALLATION AT YOUR OWN RISK![/COLOR]**

---

### Post by leosubhadeep on 2012-08-03
Hi utsav_ubuntoo,
- Are you done with your installation?

---

