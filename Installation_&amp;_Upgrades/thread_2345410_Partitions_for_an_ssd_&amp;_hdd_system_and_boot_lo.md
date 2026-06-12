---
title: "Partitions for an ssd &amp; hdd system and boot loader"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by mojo1276 on 2016-12-03
I am a first time Linux user so this is all still a learning process for me.

I have been trying to install Ubuntu 16.04 onto my brand new custom built system in a setup consisting of and 256 gb ssd boot drive and a 2 Tb hdd drive for data.  Both drives are brand new, so there have never been any other OS on them to worry about.  However I want to leave room for an eventual install of Win 10 alongside Ubuntu.  Initially I had installed Ubuntu successfully onto only the ssd, as I didn't have the hdd yet.  After I received my hdd I attempted to move my* /home* to the hdd, but either the instructions I followed were wrong or I messed up somewhere as I could get to the log in screen but every time I entered my password it wouldn't log in, it would just recycle back to the log in screen.

So because I didn't really have any important data saved yet, I decided to just reinstall Ubuntu from scratch and use the "Something else" option to partition the drives to how I want them.  This is how I have set them:
[I]
/dev/sda  <-- ssd
[/I][INDENT]*/dev/sda1   * [I]/
[/I][/INDENT]
[INDENT][I]/dev/sda2   swap
[/I][/INDENT]
[INDENT][I]/dev/sda3   /boot
[/I][/INDENT]
[I]
/dev/sdb <-- hdd
[INDENT]/dev/sdb1    /home[/INDENT]

boot loader location: /dev/sda

[/I]Is this the correct way to set this up or am I missing something?  When I have tried this I get the error of GRUB not being able to be installed to the /target/ location. I have also tried without */dev/sda3* and I got the same results.  I have also tried the boot repair tool.  Articles I found on this error have not helped as they don't seem to be able to be applied to my specific circumstance.

Basically my question is what partitions need to be created and what would the mount points be to setup an ssd boot drive and hdd data drive, as I have run out of ideas and endless searching as not yielded me any decent results?

---

### Post by kpatz on 2016-12-03
You don't need a separate /boot partition unless you're encrypting your root partition.

When you select "something else" during install and set up the partitions and tell the installer what each partition is for (i.e. /, /home, swap etc.) it will create the file systems and the /etc/fstab for you.

---

### Post by wildmanne39 on 2016-12-03
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2016-12-03
If a brand new system is it not UEFI. Your partitions look like a BIOS/MBR configuration. 
Your can use the 35 year old BIOS/MBR configuration if you want.

With both Windows & Ubuntu how you boot install media is then how it installs, either boot UEFI and install UEFI or boot BIOS and install in BIOS boot mode.

Both Windows & Ubuntu need to be installed in same boot mode.

Windows only installs in BIOS/MBR boot mode to a primary NTFS partition with the boot flag. But you have to old 4 primary partition limit with MBR(msdos).

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

I do not have Windows, but my partitions are a bit more advanced as I keep / (root) at 25GB and have all data in a /mnt/data partition. I then keep /home inside / as it has no data, just some of the hidden configuration settings.

       
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 
           
 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
           
 [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

