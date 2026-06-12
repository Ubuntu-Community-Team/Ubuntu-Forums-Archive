---
title: "the partitions don't appear in the installation"
date: 2018-08-05
forum: Installation &amp; Upgrades
---

### Post by javiercaballero on 2018-08-05
Hi there!I'm trying to install ubuntu (latest version) in a laptop with windows 7 running in legacy mode.
I've changed everything in the BIOS (change to uefi mode,disable intel rapid start,etc)
I can see the partitions with gparted but during the installation they aren't listed.
what else can I do?Thanks in advance for your help guys!

---

### Post by oldfred on 2018-08-05
If Windows 7 is legacy, you do not want UEFI unless you want to totally reinstall Windows 7 in UEFI boot mode. 
Windows only boots from MBR partitioned drives with BIOS.
Windows only boots from gpt partitioned drives with UEFI.
So if you install Ubuntu in UEFI mode, it may convert to gpt and break Windows.

Most Windows 7 installs use all 4 primary partitions with MBR, one of advantages of gpt is the limit is 128 partitions.
Post this from live installer:
sudo parted -l

Also grub only boots working Windows using Linux NTFS driver. So if Windows has issues like needing chkdsk then installer may not see any NTFS partitions.

If issue is the 4 primary partition limit, you can read ahead, but best to wait until we see what partitions you now have.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

