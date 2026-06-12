---
title: "Install to computer with no drives"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by vafred69 on 2011-02-06
Hello great folks,

Normally I can find the information I need without asking this is not one of those times.

I am trying to install 10.04 LTS on a Dell Latitude CS/x which has no CD, Floppy and the Bios will not permit to BOOT FROM USB even in the docking station.

What I've tried:

Create a small 4Gig partition on the drive from a USB to IDE interface and install the StartUp Disk to this partition, Then installing that drive in the laptop. Then trying to install a full system to another partition on that drive.

This will not work because when the installation tries to run it fails while checking drives and tells me that it cannot modify the partitions because the drive cannot be unmounted. The partition with the Startup disk is installed shows up as a /cdrom.

I can boot to the startup disk partition although the install fails due to not being to unmount and modify the partition table.

I guess what I'm looking for is a way to Pre-Install the system with my USB to IDE converter on my other laptop and remove and install this drive in the other laptop and be able to boot to it.

Is there a way to install and then continue the setup such as hardware detection on the new laptop.

I hope I've explained this so it is understandable. Any help would be appreciated. I'm not a complete noob but some type of a step by step or howto would be really helpful.

Thanks in advance,

Fred

---

### Post by dino99 on 2011-02-06
if you have or can set a network:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

what you need:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

i cant see reason why you cant install ubuntu on that drive if you plug it into an other laptop/pc: dont forget to install grub-pc on it of course, and remove xorg.conf if it exist (sudo rm /etc/X11/xorg.conf), then plug that hdd back to the Latitude

---

### Post by vafred69 on 2011-02-06
Dino99,

Much thanks. I used the USB adapter to do an install from a Live CD and so far I've been able to boot the drive in the new computer although I had to startx manually at boot although I'll figure that out. As I'm writing this the machine is performing all updates.

Seems that I needed a wired connection as the Linksys PCI card does not seem to be working yet but I'll work on that once the updates are done.

You were a great help and I will post my results in a while.

Enjoy and Be Safe. Super Bowl Day... Yahoo!!!!

---

