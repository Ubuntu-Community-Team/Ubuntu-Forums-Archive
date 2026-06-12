---
title: "Install full working Ubuntu 12.10 to a 32Gbyte USB stick"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by safetycritical on 2012-11-25
I'm trying to install a full working Ubuntu 12.10 to a 32Gbyte USB stick. I'm trying to do this from a bootable 4Gbyte usb stick containing the installation version of Ubuntu. Are there any instructions on how to do this? The installer just has an option of "something else" and then I'm presented with a list of hard drives and paritions. I'm not sure how to progress from here. I know I need to create some partitions but I'm not sure how many, what size or how to create them!! I'm using a windows 8 laptop to do this and don't want to touch the hard drive with windows 8 on it. Hope you can help :)

---

### Post by DuckHook on 2012-11-25
Installing a full working version of any OS to a USB stick is highly unrecommended. The problem is that USB sticks are comprised of a type of memory that has strictly limited number of writes after which the memory dies from write fatigue. While this number is usually in the hundred thousand writes or so, this number is easily reached in certain regions of the stick used for, say, filesystem tracking or journaling. After that, your filesystem basically becomes inaccessible. Dynamic OSes are designed to run from HDD where the base magnetic media can stand up to billions of writes with minimal deterioration. This is why USB stick-based distros all run basically as Live-CD type devices with a section set aside for persistent data. The OS is actually all loaded into RAM at startup and only user files are saved to disk. Best of both worlds, so to speak.

If you insist on installing dynamic OS to USB stick knowing full well the dangers and limitations (as an experiment, for example), then this can be easily done by selecting a different drive at install. The USB will show up either as SDB (instead of SDA, which is your HDD) or some other drive label. Incidentally, the limited write limitation does not apply to external USB *drives*, which are proper HDD drives built on classical magnetic media. The only problem installing to external USB drives is the potential fragility of the USB connection, which is an unrelated problem.

---

### Post by oldfred on 2012-11-26
I do not think it is quite as bad as Duck Hook makes it out. But flash drives are not as durable. You can and should make some settings to reduce writes to help life and speed. Flash install will not be speedy but should be functional. I use my 16GB flash just as another backup way to boot. I have 8GB for my install and 8GB for data.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Should not be much difference with 12.10.
       Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

    Some suggest the lighter weight install, so less data has to be loaded. If you have lots of RAM, once loaded it does not matter much as RAM caches recent activity.
       HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

    
The install is just like any install to a second drive. You have to use Something Else and manually partition as on the partition screeen is the combo box on where to install the grub2 boot loader. And you have to install to sdb (or sdc) or whatever drive the install is into. Any auto install options just install grub to sda.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

    
       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by DuckHook on 2012-11-26
Choose oldfred's suggestions over mine as he is far more knowledgable. I will also implement his suggestions on a USB stick as it has long been a wish of mine to create my own custom repair stick. Only question: is ext2 acceptable over ext4 sans journaling?

---

### Post by oldfred on 2012-11-26
I just took ext2 out as my suggestion as 12.10 seems to have some issues with ext2. I think I saw a related bug but was not even sure it applied, but it seemed to be related to any filesystem without a journal. I do not have 12.10 on my flash drive yet.

I also put many ISO as additional repair tools in my data partition on my flash drive.

  This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

