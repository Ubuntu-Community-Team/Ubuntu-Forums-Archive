---
title: "Ubuntu 16.04.3 installs/Won't boot"
date: 2018-02-08
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2018-02-08
Been trying to install Ubuntu 16.04.3 for a couple days now. The old hard drive had Ubuntu 14.04 and worked flawlessly. I removed the old drive and installed new 2TB drive. Booting from the DVD with Ubuntu 16.04.3 works great. I installed it on the new drive and it won't boot. Boot repair info is here.  [http://paste.ubuntu.com/26541992/](http://paste.ubuntu.com/26541992/)

Before, boot repair said I installed in EFI mode but that I'm running in legacy mode. This is an older mobo from 2008. It does not have UEFI mode nor windows fast boot. It is an MSI mobo with 8 geg's of ram. The PC bios sees the 2 TB drive. Ubuntu Gparted and Disks utility both see the drive. Yet when I boot up, I get a boot option screen that only shows the DVD as a boot option and not the new hard drive.

sudo lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1.5G  0 rom  /cdrom
loop0    7:0    0  1.4G  1 loop /rofs
sda      8:0    0  1.8T  0 disk 
&#9500;&#9472;sda2   8:2    0    1K  0 part 
&#9500;&#9472;sda5   8:5    0    8G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0  1.8T  0 part 
sr1     11:1    1 1024M  0 rom  

Any ideas?

Many thanks all.
Magpie

---

