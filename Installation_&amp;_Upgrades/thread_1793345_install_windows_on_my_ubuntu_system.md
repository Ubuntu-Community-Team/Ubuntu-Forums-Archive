---
title: "install windows on my ubuntu system"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by preacherles on 2011-06-29
I have ubuntu 10.04 and I love it.  I just opened up a business and I need to use windows.  The software will not work on ubuntu.  How can I install windows xp along side of my ubuntu system?

---

### Post by snowpine on 2011-06-29
There are a couple of different ways to do it, here's what I do:

Assuming your hardware is pretty fast/powerful, you can install VirtualBox in Ubuntu and then install Windows XP as a "guest" operating system inside of a virtual machine. This gives you the speed and stability of Ubuntu for your everyday tasks, and when you need the Windows-specific software, you just switch to the virtual machine. Best of both worlds. More info at [www.virtualbox.org](www.virtualbox.org)

The other option of course is to install Windows on its own partition as a "dual boot." This will kill your GRUB bootloader, so once Windows has been installed, you'll have to reinstall GRUB2. Instructions for doing this are on the Ubuntu Wiki (I haven't done this personally so I don't have details, sorry). The drawback to a dual boot is that you can only use one of the operating systems at a time; you need to reboot to switch between them.

Good luck! :)

---

### Post by preacherles on 2011-06-29
Is there any way to make a new partition and install the windows?  I have had this since 10.04 came out and have done a lot of tweaks to it.  I don't really want to delete everything if I don't have too.  I cannot use a virtual machine either.  I would love to be able to just install windows on a separate partition if at all possible.

---

### Post by oldfred on 2011-06-29
Do you have a primary partition available?

Windows has to install to a NTFS primary partition formated to NTFS with the boot flag (active partition in windows) or to unformated space with a primary partition available, usually a blank drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by YesWeCan on 2011-07-01
> **preacherles said:**
> I have ubuntu 10.04 and I love it.  I just opened up a business and I need to use windows.  The software will not work on ubuntu.  How can I install windows xp along side of my ubuntu system?
A couple of purely optional tips:
(always back up any vital data before modifying partitions)

1) For future flexibility it is handy to have all your Ubuntu partitions inside one extended partition. If it is not set up like this you can use GParted on live CD to rearrange things.
- make en extended partition if there isn't already one and resize it as needed
- copy and paste your Ubuntu partition(s) into it.
- sudo blkid to determine the UUIDs of your new partitions. Edit /etc/fstab accordingly.
- re-install Grub (eg: your new Ubuntu /boot is in sda6):
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
- Once it works, delete the old partitions

2) Sometimes using dual-boots with Windows on the same disk can cause MBR conflicts. If XP repairs the MBR then Grub won't work. It is very easy with XP to add Grub's boot code to XP's boot-loader menu. So you always boot into XP and then choose Ubuntu.
- before installing XP, copy the Grub boot code to a file
sudo dd if=/dev/sda bs=512 count=1 > grub.bin
- then install XP
- then boot Ubuntu from live CD and copy grub.bin to the c:\ folder
- boot XP and add this line to boot.ini:
C:\grub.bin="Ubuntu"

---

