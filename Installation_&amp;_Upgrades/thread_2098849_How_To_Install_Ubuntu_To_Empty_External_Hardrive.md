---
title: "How To Install Ubuntu To Empty External Hardrive"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by Austrie on 2012-12-27
Hey Ubuntu forums, here comes a active member to the community since I'm going to use Ubuntu as my main OS.

WELL my native hard drive failed, so I'm going to go buy a external USB hard drive from RadioShack sometime this week. I installed Ubuntu 10.04 on my usb flash drive last year and still have it. It works for my other 2 computer but it doesnt work with the one with the failed hard drive anymore after the hardrive failed, I keep getting /dev/sr0: no medium found error. So how do I install Ubuntu to this empty external USB hard drive?

---

### Post by C.S.Cameron on 2012-12-28
Plug your external hard drive into one of your other two computers after disabling the internal hard drive and install to the external from there.
You will be ok as long as you don't install any proprietary drivers while connected to the other computer.

You can move the external from computer to computer just like a Live flash drive.

---

### Post by Austrie on 2012-12-28
Thanks Ima try it once i get the HDD. Is there any other way/easier way?

---

### Post by C.S.Cameron on 2012-12-28
> **Austrie said:**
> Thanks Ima try it once i get the HDD. Is there any other way/easier way?

You could try using the Live CD.

---

### Post by aspergerian on 2013-01-02
I too would like to install a Canonical flavor on external HD that would be connected to either an HP G71 or an HP dv7, each running Windows 7. 

CS Cameron counseled "Plug your external hard drive into one of your other two computers after disabling the internal hard drive and install to the external from there. You will be ok as long as you don't install any proprietary drivers while connected to the other computer."

I've read numerous threads about installing on external HD. (Indeed, way too many) Most say disconnect the boot HD in the computer hosting the installation process. Some threads or pages have said that the disconnect is not absolutely necessary - while warning a) not to allow writing to the installtion-computer's master boot record record, and b) not to install to the installation-computer's HD. 

I have mild Parkinson's and have too much tremor to dare disconnect one of the HP's internal HD, so would prefer to install (probably 12.04 Xubuntu or 10.04 Ubuntu) without disconnecting a notebook's internal HD. 

Perhaps I'm looking for best-urls for the installation procedure I prefer. Confused and hesitant, willing to learn. Suggestions or instructions appreciated.

---

### Post by oldfred on 2013-01-02
The important issue with installing to a second drive is the choice of where the grub2 boot loader is installed. You want it in the MBR of the external drive. 

All the auto install options will default to installing grub to sda, which is usually the internal drive. While it can be repaired later, it is much better to install correctly during the install.

But then you have to use manual install, create partitions (or choose partitions you made with gparted before), select mount / (root), /home, swap etc and formats. On that same partitioning screen at the bottom is a combo box which shows all drives and partitions. Do not install to partition and choose same drive as you are installing to for installing grub. See Herman graphic below or Linuxbsdos graphic about half way thru.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer (12.10 does not have text based installer).
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

The alternative installer is text based, but looks very similar to the gui installer.

A suggestion on partitioning, but it depends a lot on what you want to use system for:
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by aspergerian on 2013-01-02
oldfred,

Thank you for the detailed reply. I'll be studying it as I move slowly forwards with my ext HD project. Today, testing Xubuntu 12.04 worked on th HP G71 but didn't find wifi signals on the HP dv7.

---

