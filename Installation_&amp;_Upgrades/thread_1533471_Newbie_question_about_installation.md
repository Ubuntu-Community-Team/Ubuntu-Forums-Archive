---
title: "Newbie question about installation"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by goldberg96 on 2010-07-18
Hi all. I have just completed a Linux Essentials training course that my company sent me to. I decided I wanted to try a Linux desktop at home. I have a pretty beefy computer setup at home. I have two extra SATA II hard drives on my system. My primary system is currently Windows XP Professional. I want to install Ubuntu onto one of my spare drives and then have it be bootable. But every time I try to install the OS it just shows me my system drive that already has my windows system on it. Can someone please explain the basic process to me of how I install the Ubuntu OS onto another hard drive so that each OS is on a separate hard drive on my system? I seem to be stumped getting that task accomplished.
 
Thanks all ........... Rob

---

### Post by claracc on 2010-07-18
Perhaps the tutorial in this thread [http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives](http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives) can help you.

Regards

---

### Post by goldberg96 on 2010-07-18
The problem is that when I boot the live cd and try to install, the only drive it offers me is the drive that my Windows XP system is on. These are all SATA drives. I have four of them and two of them are empty (although previously formatted as NTFS). Is there something I have to do in my BIOS for the drive I want to use. My BIOS seems to only have room for three entries in the boot order and currently they are set to 1) CD drive, 2) floppy drive, and 3) Hard drive with Windows on it. The BIOS sees all of my drives however if I look at the disk drive configuration.

---

### Post by pastalavista on 2010-07-18
> **goldberg96 said:**
> Hi all. I have just completed a Linux Essentials training course that my company sent me to. I decided I wanted to try a Linux desktop at home. I have a pretty beefy computer setup at home. I have two extra SATA II hard drives on my system. My primary system is currently Windows XP Professional. I want to install Ubuntu onto one of my spare drives and then have it be bootable. But every time I try to install the OS it just shows me my system drive that already has my windows system on it. Can someone please explain the basic process to me of how I install the Ubuntu OS onto another hard drive so that each OS is on a separate hard drive on my system? I seem to be stumped getting that task accomplished.
 
Thanks all ........... Rob

Can you boot the live CD and try Ubuntu? If so, make a partition (System-> Administration-> GParted) by shrinking (or deleting.. but don't delete C:\) the formatted space of one of your drives (you'll have to unmount it first) and reformat an extended partition in the empty space as ext4 or ext3. Then click the install icon on the desktop and when you reach the partition process, select manual mode and create logical partitions for '/' and 'swap' mount points and a '/home' partition, if you want to separate your data from system files.

edit: that is, if you can see the separate drives in Ubuntu with GParted or Disk Utility

---

### Post by goldberg96 on 2010-07-18
OK, maybe I'm being really think here but i don't quite get it. If I have completely empty drives on my system and I want to use one of them, why would I have to be involved in doing additional partitioning work? I can boot up Ubuntu. When I try to install, the only drives I am presented with as an option for formatting and installing are my system drive (Windows system) and my USB drive (which is only for backups). My other three SATA drives don't get listed so I can't select one of them for formatting and installation. The problem I need to solve is determining why my other SATA drives are not being presented as choices for installing the Ubuntu OS.

---

### Post by pastalavista on 2010-07-18
If you only see one drive in the MANUAL formatting mode of the Ubuntu installer, your drive might be RAID formatted, but you can't install Ubuntu in a Windows filesysytem unless you use the Wubi installer. Just load the CD in Windows.

---

### Post by dino99 on 2010-07-18
be sure that your bios is set with ahci mode, and your hdd not running fakeraid:

sudo dmraid -r -E /dev/sdx (where sdx is your disk)

[http://ubuntuforums.org/archive/index.php/t-1500146.html](http://ubuntuforums.org/archive/index.php/t-1500146.html)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

