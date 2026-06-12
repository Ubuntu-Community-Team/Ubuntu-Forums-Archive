---
title: "dual boot ubuntu and windows 7 on alienware m17x r4 without using raid"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by rpasia on 2013-08-09
Can someone please guide me how I should go about setting up my alienware m17x r4 to dual boot windows and ubuntu? I would like to install ubuntu on the first ssd and windows on the 2nd ssd. It's has some kind of RAID setup, which I do not want. What steps do I take? Thanks.

---

### Post by oldfred on 2013-08-10
I would put Windows on the first and Ubuntu on second, but that may be just which port each drive is plugged into.

You have to change BIOS to AHCI if it is in RAID and remove the RAID meta-data from drives.
       sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

I like to keep each system totally separate or the install on sda also has the boot loader for sda, and install on sdb has boot loader for sdb.

Windows installs its boot loader to the drive you boot from in BIOS. So reset BIOS to boot the Windows drive or else it will put a (hidden) 100MB boot/recovery partition on the BIOS boot drive.

Ubuntu always installs its boot loader to sda (which usually is the boot drive). The only install option that gives a choice is Something else or manual install. And on the partitioning screen at the bottom is a combo box to chose which MBR to install the grub2 boot loader into.

Above is all for BIOS install. If UEFI it is somewhat different.

These are the only two examples I have seen showing a second drive. Version is not critical as all recent versions are installed the same way with only slight differences in graphics.


 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by rpasia on 2013-08-10
Thanks for the advice, oldfred. I will definitely read up and try!

---

### Post by Brian_Ask on 2014-03-25
I know this may be a little late, but I have installed Ubuntu on my Windows 7 Alienware system several times now, and I can tell you the best method I have found is to use Wubi. 

Wubi installs from Windows, allows you to choose your installation drive/partition and size, and most importantly, edits your Windows Master Boot Record to add Ubuntu as a boot option. Wubi installs a presized folder on the drive/partition you choose, so there's no need to use a separate drive if, like me, you want to install it on your faster Solid State drive. Note: Just make sure you don't delete the folder or the grub files through Windows.

This has proved far less troublesome than any other method I've tried and doesn't mess up Windows at all - even if you decide to remove Ubuntu at a later date, you can simply delete the folder and edit the MBR through Windows. 

Wubi does install 12.04 but you can update it afterwards, just tell it to skip when it complains it cannot edit the grub.

---

### Post by oldfred on 2014-03-25
That is what wubi is for, but all new computers use UEFI with gpt partitioning. Wubi does not work with gpt partitioning so 12.04 is the last supported version of wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can install Ubuntu to a flash drive, not quite as fast but functional if some settings to reduce writes are changed. Now older but still same procedure.
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


---

