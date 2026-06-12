---
title: "arch, gentoo and ubuntu in one dvd?"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by khaj_vah on 2012-04-22
Hello people,

I am not quite noob and i am not experienced in linux but i already love it. Anyway, i want to make a dvd disk with which i can install arch, gentoo or ubuntu, but i know that just putting files on that dvd won't help. I need something like GRUB, so i can choose which OS to install (boot), at the start. Is it even possible? I think it is possible but i need help. 

Thanks for help.:)

---

### Post by jadtech on 2012-04-22
not sure  what you are looking to do is possible , it is possble to pt more then one image on a dvd there are programs you can buy to if it takes more then one iso image for an install ..

if you are looking to make Live bootable images only the frist image would be bootable ...

---

### Post by oldfred on 2012-04-22
I have not tried CD or DVD. And not installs work from a multiple installer easily.

CD/DVD multiboot
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

I have installed multiple versions of Ubuntu and several others to loopmount with grub2 from a flash drive. I did this before some scripts became available to automate the process to flash drives.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

---

### Post by khaj_vah on 2012-04-23
> **oldfred said:**
> I have not tried CD or DVD. And not installs work from a multiple installer easily.

CD/DVD multiboot
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

I have installed multiple versions of Ubuntu and several others to loopmount with grub2 from a flash drive. I did this before some scripts became available to automate the process to flash drives.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
Thanks very much, i will try soon :)

---

