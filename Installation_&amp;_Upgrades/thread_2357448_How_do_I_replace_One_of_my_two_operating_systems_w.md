---
title: "How do I replace One of my two operating systems with Ubuntu?"
date: 2017-04-02
forum: Installation &amp; Upgrades
---

### Post by jahva7 on 2017-04-02
Hi Everyone. I have 2 operating systems on my netboot: **Windows 7 professional** and **Windows 7 Starter**. And I would like to replace windows 7 starter with Ubuntu, but keep windows 7 professional. How should I go about doing this? (without the CD and USB burning stuff) I want to use Wubi. Is this possible and if so, how should I do it? 

Ps. I am new here to this forum. This is literally my first post and I have never used linux before. this will be my first time to use linux if I am successful with the installation. I am hoping it will make my samsung netbook faster, so I can get some school work done.

---

### Post by oldfred on 2017-04-02
Wubi is obsolete. And last supported version was 12.04 which is about to be obsolete and probably does not support most newer hardware.
And wubi is configured as a Linux partition inside your NTFS partition. Would not be as fast as a full install anyway.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239)

Is Windows 7 UEFI or BIOS. Most Windows 7 installs are the old BIOS/MBR configuration with the 4 primary partition limit.
       
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

Also note that Windows only boots thru the one primary NTFS partition with the boot flag. If you delete that partition then neither Windows will boot.
Post this from Ubuntu live installer's terminal:
sudo parted -l

       Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

