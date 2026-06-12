---
title: "ubuntu 14.04.03 64 bit installer will not recognize windows 10 OS"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by drudisaile on 2015-09-10
I am trying to dual boot windows 10 and ubuntu.  I  have created the ubuntu 14.04.03 64 bit install DVD and when I try to install it I get a message stating that there is no detected OS.  I have already created a separate 100gb partition specifically for use for ubuntu which is ready to go.  Any help on how to address this issue would be greatly appreciated!

---

### Post by oldfred on 2015-09-10
Did you turn off fast start up in Windows?
Did you turn off fast boot in UEFI (if UEFI system)?
Have you backed up Windows & your data?
Have you made a Windows repair flash drive? Grub only boots working Windows.

Is Windows UEFI or BIOS?
Did you create ext4 partition for Ubuntu and swap partitions? You cannot create those from Windows.
Post this from terminal in live installer:
sudo parted -l

       UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html
[/URL]
 But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)

[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]
[/URL]

---

### Post by drudisaile on 2015-09-12
Thank you for posting the above links.  I have now successfully set up my system to dual boot windows 10 and ubuntu!

---

