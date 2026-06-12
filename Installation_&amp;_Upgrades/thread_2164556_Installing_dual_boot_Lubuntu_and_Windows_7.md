---
title: "Installing dual boot Lubuntu and Windows 7"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by Melonman01 on 2013-07-31
Having a few issues doing the above on my netbook. Courtesy of Korean internet stupidity I need Windows to run Internet Explorer. I was under the impression that if I installed from a USB, I would be able to partition my hard drive with a slider, and have the option of installing Lubuntu beside Windows 7 (as per the 'installation type' window described [here]("http://launchintolinux.wordpress.com/2012/04/04/installing-lubuntu-a-step-by-step-guide-to-dual-booting/")). Instead, I get a much more concerning 'installation type' window asking me if I would like to a) erase everything and install Lubuntu or b) if I would like to do something different involving partitions and such. There is no mention of installing Lubuntu alongside Windows 7.

What do I need to do in order to run a dual boot version of Lubuntu and Windows 7?

---

### Post by oldfred on 2013-08-01
Almost all Windows 7 systems use all 4 primary partitions. You need one primary to convert it to the extended partition and then inside the extended can create as many logical partitions as you want. Most find a vendor utilities/tools partition as the easiest to backup, some are available as a download if lost, and most can be put back as a logical if you want. Some also create the vendor recovery DVD and then do not need recovery partition. Do not delete the (hidden) 100MB Boot partition nor the main install partition.

Use Windows tools to shrink the main c: drive partition and reboot Windows so it can run checkdisk. Then if you just want the standard / (root) and swap it will offer to autoinstall into the unallocated space. Or you can manually partition if you want separate /home or another NTFS data partition for shared data (recommended).

Be sure to fully backup Windows & its boot partition and make a Windows repairCD or flash drive.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

      
 Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)


 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bucky Ball on 2013-08-01
*Thread moved to **Installation & Upgrades**.*

Welcome to the forums.

---

### Post by Melonman01 on 2013-08-01
Wow, thanks guys. I've never had to partition stuff on a PC (done it before with a Mac) so I'll give the partitioning stuff a crack next week I think, when I have a bit more time. Related question: how is Lubuntu at dealing with files (image files, specifically?). I was planning on using Windows for Internet Explorer only and Lubuntu for everything else; my GF and I are travelling and this little netbook is all we have. Will it deal faster and more reliably with JPEGs than Windows 7 will? If so, I'll probably make the dedicated Lubuntu partition the majority of the hard disk.

---

### Post by Topsiho on 2013-08-01
Thanks to oldfred for this very neat overview (howto) of how to install an Ubuntu next to Windows7 !!!

I copied this, for when I 'll have to try and do this myself :)

Topsiho

---

### Post by Bucky Ball on 2013-08-01
If you are intending to dual-boot you should probably create a data partition that is NTFS to share data between the two (Windows will not read the EXT* Ubuntu partition but Ubuntu will read NTFS fine. So, you would need a small, 15Gb partition for Ubuntu, a partition for Windows and keep all personal information on a partition the size of the rest of the disk, perhaps.

You may have mentioned this, but, is there a reason you need to use IE?

---

