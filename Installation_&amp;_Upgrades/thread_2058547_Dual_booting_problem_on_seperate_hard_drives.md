---
title: "Dual booting problem on seperate hard drives"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by isobitis on 2012-09-15
Hi,

I decided to install Ubuntu 12.04 on my Win7 desktop PC. I have 2 internal hard drives (120GB the first and 1TB the second one). My Win7 was installed in one partition on 1TB and I wanted to put Ubuntu in other hdd. I did it (partition /swap, /home and the root), Ubuntu worked fine but Win7 didn't boot. After trying all possible methods (repair, command prompt with all /fix solutions, inactive partitions and generally whatever I could find about these booting issues), I decided to format Win7 disk. After this (and new problems because Win7 installation DVD doesn't recognize the 1TB formatted disk but only when I erased Ubuntu from the other disk) I reinstalled Win7 on my 1TB.
Now, I want to reinstall Ubuntu but I prefer to avoid mess up my Windows Installation again.

My 120GB is my /sda disk and 1TB is /sdb.
When I try to change disk order in BIOS, system doesn't boot (Media failure error).
So, the situation is:
120GB disk as:
/sda1 ~100MB ntfs (Windows7 loader)
/sda2 free space (for Ubuntu installation)
1TB disk as:
/sdb1 100GB ntfs (Windows 7 Installation)
/sdb2 900GB ntfs (for my data)

I want to format the /sda2 space but which disk to select for bootloader (grub) installation?
Is there a proper way to install Ubuntu and create a dual booting system with disk and partitions structure I described? 
I know that was best choice the 120GB hdd for Win7 installation but as a newbie in Linux I realized that after second installation of Win7 and when noticed that Win7 loader was on 1st hdd...! 

Thanks in advance!

---

### Post by oldfred on 2012-09-16
Welcome to the forums.

You can install grub2's boot loader to either drive and just set BIOS to boot from that drive. You have to use manual install or something else to get the choice on which drive's MBR to use to have grub2's boot loader.

I generally prefer with multiple drives to have each system fully on one drive including boot loader, so when a drive fails the other drive still can be booted. If parts are on both drives then any failure prevents booting of hard drives. Be sure to have current version liveCD for Ubuntu and repairCD for Windows just in case a drive does fail.

Generally you install Windows to sda  and sda is the boot drive in BIOS. Windows then installs its 100MB hidden boot/repair partition to sda and main install to sda. But if you still have sda set as boot in BIOS and install Windows to sdb, it will put the 100MB boot partition on sda.

---

### Post by isobitis on 2012-09-16
Hmmm.... Yes... I saw it yesterday after Win7 Installation...! A little bit late!! :O 

I think to install Ubuntu on sda or reformatting disks (I didn't make a lot of stuff to Win7) and install it fully seperate as you suggested in second paragraph. It depends on mood, I guess!

Thanks a lot for your help! :smile::smile:

---

