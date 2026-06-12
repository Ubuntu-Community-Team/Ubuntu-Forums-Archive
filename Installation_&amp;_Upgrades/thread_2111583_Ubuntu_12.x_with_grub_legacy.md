---
title: "Ubuntu 12.x with grub legacy"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by Paranoid Geekazoid on 2013-02-02
I currently have Ubuntu 9.04 with GRUB (version 0.x) installed in /dev/sda2 (Windows is installed on /dev/sda1).  I would like to keep this version of GRUB (and keep it on /dev/sda2 and not the MBR) and simply upgrade Ubuntu.

Is that possible and how?

If not, I would accept having to install GRUB2 on /dev/sda2.  The main / critical thing is not to disturb the non-GRUB bootloader currently residing in the MBR.

---

### Post by oldfred on 2013-02-02
I happen to like grub2, but did not like it at first as it was a big change from grub legacy and not well documented in the beginning.

Grub legacy still is in the repository and can be installed, but the Ubuntu installer will auto install grub2. Default installs auto install to sda, so you have to use a manual install or Something Else to get the option on where to install grub2's bootloader.

Grub2 can be forced into a PBR, partition boot sector. But it has to convert to blocklists since grub2 is larger than old grub legacy to accommodate all the new computer features. Major updates where grub2 gets updated may move files on drive and blocklist entry will be wrong. So grub2 has to be reinstalled into the PBR on some major updates. Or have liveCD handy to fix if need be.

If your system is older and you do not do any special install with new partition formats or RAID, LVM, UEFI etc then grub legacy should still work. It just is that grub legacy has not been updated for years. Ubuntu even modified its version of grub legacy 0.97 in 9.04 to work with ext4.

Uninstall grub2
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by grahammechanical on 2013-02-02
This is not something that I have noticed as I only have one hard disk and whenever I do a test install of the latest ISO image I let the install process do its default stuff (put Grub into MBR /dev/sda) But, 

I seems to remember that when we get to the partitioner part of the install, where we select the partition to install to and the file system type, etc., there is an option to select where to install Grub. It is a panel with a drop-down menu underneath the main panel which lists the partitions.

I will try to find an image to link to. Here is one. Move down the page to the fifth image headed Allocate Drive Space. See the panel called Device for Boot Loader Installation. We can change the default location of Grub.

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

Regards.

---

### Post by Paranoid Geekazoid on 2013-02-02
> I happen to like grub2, but did not like it at first as it was a big  change from grub legacy and not well documented in the beginning.Personally, I think the menu system is overly complex, but maybe it's more scriptable this way?
 
> Grub legacy still is in the repository and can be installed, but the  Ubuntu installer will auto install grub2. Default installs auto install  to sda, so you have to use a manual install or Something Else to get the  option on where to install grub2's bootloader.Right, so if I explicitly instruct it to install to /dev/sda2, it will leave the MBR completely untouched?
 
> Grub2 can be forced into a PBR, partition boot sector. But it has to  convert to blocklists since grub2 is larger than old grub legacy to  accommodate all the new computer features. Major updates where grub2  gets updated may move files on drive and blocklist entry will be wrong.  So grub2 has to be reinstalled into the PBR on some major updates. Or  have liveCD handy to fix if need be.That's OK, I don't want a separate boot partition.
 
> If your system is older and you do not do any special install with new  partition formats or RAID, LVM, UEFI etc then grub legacy should still  work. It just is that grub legacy has not been updated for years. Ubuntu  even modified its version of grub legacy 0.97 in 9.04 to work with  ext4.My system is fairly new, but I've disabled UEFI.  I'm currently running GRUB legacy in Ubuntu 9.04, but it's too old and it doesn't have any of the drivers for the VGA or networking.
 
> Uninstall grub2
 [https://help.ubuntu.com/community/Gr...ing%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")
 
 HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
 [https://help.ubuntu.com/community/Gr...to_GRUB_Legacy]("https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy")
 Older threads kansasnoob
 [http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
 [http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)Thanks for the links :)

---

### Post by oldfred on 2013-02-02
I try to maintain only two kernels and turn off the os-prober since on my desktop I have many old and a few test installs. Then I create a 40_custom with just the entries I want.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

    
       Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

    
       From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

---

