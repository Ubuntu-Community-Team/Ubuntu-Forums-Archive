---
title: "Persistant USB Installation"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by pogopope on 2011-10-17
Brief overview: I recently purchased a 64gb flash drive and have been trying various methods to create a persistent Ubuntu installation while leaving a majority of the space on the drive as a fat32 partition so I can continue to use it with windows as well.

My installation method consists of booting off of a 4gb flash drive containing the installation media created with a live usb creator application. I then specify the partition table during installation and allocate the first partition as a 55gb fat32 filesystem. The remaining ~8gb is allocated for the root ext4 filesystem which is marked as bootable. It's important to note that the fat32 partition must be the first partition on the disk or Windows will not recognize it properly (it will see the media but won't think that it's formatted appropriately as fat32).

I choose to install grub to the root filesystem (bootable 8gb ext4) and the installation completes successfully. At this point I verified that Windows can interact with the fat32 partition and the box I originally used for the installation can boot from it.

However, when I attempt to boot other systems from the flash drive they do not recognize any bootable partitions. My second laptop for example, which dualboots Win7 and Ubuntu is able to boot the aforementioned 4gb installation flash drive but the TrueCrypt bootloader doesn't recognize the 64gb flash drive as being bootable.

If anything about this scenario throws any immediate red flags please share. Additionally, if you've managed to create a persistent flash install with the following conditions please feel free to share how you accomplished it.

*Must be upgradeable and persistent
*Must be able to utilize fat32 partition for Windows use

Thanks in advance for any guidance.

---

### Post by oldfred on 2011-10-18
If you are using Truecrypt there are lots of issues and I do not understand Truecrypt. You can search forum as there have been several threads recently on that topic.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

You normally install grub2's boot loader to the MBR of the flash drive so you can boot it. But that does not work with Truecrypt.

---

