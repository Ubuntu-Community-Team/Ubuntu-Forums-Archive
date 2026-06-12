---
title: "Ultimate boot USB"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by timbim on 2012-06-28
Hi All,

I've given up using live CD's for installing on systems now, preferring to use a USB formatted as a boot disk.  The only annoying thing about that is that I find myself constantly reformatting the thing to get a different distro.  I've been thinking for quite a while how neat it would be to have a single usb stick with several distros installed, and then to be able to select which one to use when the system boots off it.  So I could have a USB with ubnutu, lubuntu, fedora, ubuntu server, centos and system rescue cd all on one USB stick.

I'm thinking something of this nature might be possible with a reasonably large stick and careful use of GRUB, am I thinking right here or is this idea a no-goer.  Any hints on how I might do it?

Thanks,
Tim

---

### Post by C.S.Cameron on 2012-06-28
I think what you are looking for is MultiBootUSB,
You can boot multiple iso's on an USB drive using Grub2 and install from each.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by oldfred on 2012-06-28
MultiBoot is one, there are several, some using different boot loaders. I did it just with grub2 manually before all the scripts. You just need to install grub2 to the USB and create a grub.cfg with the correct loopmount of the ISOs. I use the same procedure not to install from one hard drive to another by adding loop mount of the ISO from a hard drive partition on a different drive.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
older MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

[http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb](http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

This will boot an ISO from a hard drive. USB drive is just another drive and drive, partition of folder with ISO is the vital boot info.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

