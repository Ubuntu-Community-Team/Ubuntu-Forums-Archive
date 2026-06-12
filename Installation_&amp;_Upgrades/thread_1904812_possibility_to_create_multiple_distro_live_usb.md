---
title: "possibility to create multiple distro live usb?"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by supermooshman on 2012-01-05
a thing I've been wondering for quite a while now,

Since from time to time I succeed in converting someone to linux, they mostly ask me what the best distro is. Even though this is a sensitive topic (less than the whole apple/windows/linux discussion) I figured, how about if I just create a live usb stick with my favorite ones?
I was wondering whether this is possible and how to go about this...

Is it possible to partition my stick and use a partition per distro, or is there more to it?

Many thanks!

---

### Post by oldfred on 2012-01-05
If you have a newer large flash drive you can install multiple copies or if installing you can use grub2 or other bootloaders to loopmount ISOs and you can fit many ISO on a flash drive. Not all distributions can be loopmount but many can.

I did this before the scripts came out to semi-automate the process.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Each script has different defaults, I have not used any of them as I already had my system set up:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by RagingLoon on 2012-01-05
I have a thumbdrive with [SARDU]("http://www.sarducd.it/") and another with [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") both are easy to setup with Ubuntu, Fedora or whatever you desire. I have well over a dozen OS'es on those two thumbdrives. SARDU is great for Windows and Linux OS'es and YUMI works awesome for Linux distros. However, my FreeBSD is housed on it's own thumbdrive and I can't remember why?


Hope this helps.

---

### Post by supermooshman on 2012-01-05
> **oldfred said:**
> If you have a newer large flash drive you can install multiple copies or if installing you can use grub2 or other bootloaders to loopmount ISOs and you can fit many ISO on a flash drive. Not all distributions can be loopmount but many can.

I did this before the scripts came out to semi-automate the process.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Each script has different defaults, I have not used any of them as I already had my system set up:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

at the moment I'm :confused: but hopefully after reading through your information I'll be :D

if not, I'll be back!
Thanks!

---

### Post by RagingLoon on 2012-01-05
> **supermooshman said:**
> at the moment I'm :confused: but hopefully after reading through your information I'll be :D

if not, I'll be back!
Thanks!

Hey, the pendrivelinux that [COLOR=#d40000]**oldfred**[/COLOR] mentioned is YUMI. It's very straightforward, just read the page on it. Down towards the botom of the page you'll see "_[List of Installable Live Linux Distributions]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/#")_" I'm sure you'll find every flavor of Linux you want right there.YUMI will take care of the rest for you. ;)[URL="http://www.pendrivelinux.com/yumi-multiboot-usb-creator/#"]
[/URL]

---

### Post by Rebelli0us on 2012-01-05
It can be done but USB sticks are cheap, so why not do **one** distro per stick. Then if they like it you can let them have the flash drive.

---

### Post by supermooshman on 2012-01-05
awesome, i will try yumi tomorrow

> **Rebelli0us said:**
> It can be done but USB sticks are cheap, so why not do **one** distro per stick. Then if they like it you can let them have the flash drive.
cheap yes, free no (actually yes, I only use usb sticks that I find and cant track down the owner)
but a single 8gb stick I can attach to my keychain, eight 1gb sticks... well let's just say I would be able to attach a key to my usbchain :P

---

### Post by C.S.Cameron on 2012-01-05
I would suggest MultiBootUSB, mentioned in Oldfred's post.

For more info see:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

