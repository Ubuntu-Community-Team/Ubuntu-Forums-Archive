---
title: "install ubuntu on second hdd"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by mattb10411 on 2013-07-12
I have a desktop with win 7 installed. I have just installed a 2nd 500gb sata hdd and would like to install ubuntu on the 2nd drive. If I do this will I still have the option to boot win/ubuntu at startup.


Ok I can probably do without having a boot option since it would probably confuse my girlfriend. I know how to go into BIOS and have it load from the new HDD. If I install it on the other drive and have BIOS load that drive first instead of win 7 drive will that interfere with windows or will it load ubuntu just fine. Also is there a site or forum that is really good for first timers to learn about how to use it. I am wanting to install this because I am just interested in learning about a new OS besides win.

---

### Post by nah40 on 2013-07-12
I did it about 5 years ago by disconnecting the windows drive, then installing Ubuntu.
Everything worked as designed, including boot options.
I am guessing it will still work that way.
There was a forum article on it at that time.

---

### Post by oldfred on 2013-07-12
Safest is to disconnect Windows drive and install Ubuntu. But you need to make sure you reinstall Windows to same SATA port so it still is sda. And after the install run this so grub2's os-prober can find Windows and add it to your grub menu.
sudo update-grub

If you do not disconnect drive you need to use Something Else and manually partition and choose formats. You must then choose to install grub2's boot loader to the Ubuntu drive, probably shown by the exact drive model number or as sdb. You want to keep the Windows boot loader on sda. It can be fixed later if need be but better to do it correctly first. All auto install options will install grub2's boot loader to sda overwriting the Windows boot loader.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I am assuming your Windows is in BIOS mode with MBR(msdos) partitioning. Only a few newer ones use UEFI which then is totally different. With Ubuntu you can use MBR or gpt partitioning as long as you do not want to boot Windows from a gpt partitioned drive in BIOS mode. Ubuntu works with gpt for BIOS or UEFI. IF MBR partitioned you can only boot with BIOS, not UEFI.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

