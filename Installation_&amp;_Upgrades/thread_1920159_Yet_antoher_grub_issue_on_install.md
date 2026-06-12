---
title: "Yet antoher grub issue on install"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by duderduderini on 2012-02-04
Hi.
My dislike for all things windows brings me back to trying ubuntu every now and then. I decided to install 11.1o according to this guide
[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)
I set up 
sda5 the /boot
sda6 the swap
sda7 the/
sda8 the /home partitions.
The install goes belly up when it wont install grub into sda5.
i am on my 5th reinstall and I havent the fogiest idea on how to get grub to install into sda5 which is a logical partition btw.
I know there is a force command for grub to install where you specify but my googling of the problem leads me to believe their is a prob with grub2.
So if i cant fix, i will stay with Mr gates masterpiece for a while again.
Many thanks to anyone that helps

---

### Post by oldfred on 2012-02-04
You do not need the /boot and have to install grub2's boot loader to the MBR. Grub has several parts. All BIOS/MBR computers boot from BIOS linking to MBR which has just a bit of code that loads the rest of the system. So you choose sda not sda5 or the hard drive for the install of grub2's boot loader.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

