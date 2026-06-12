---
title: "Ubuntu boot from CD, root from SMB"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by jsbiff on 2010-09-14
Hi,

   So, I'm trying to find out if the following is possible:

I know that the Ubuntu version called WUBI has the ability to create an Ext3 FS inside of a file in an NTFS partition and then mount that filesystem as the root fs. Now, the question I have is, would it be possible to do something like that, but where instead of starting from Windows, you start from an Ubuntu boot/install CD, then create and install the Ubuntu Ext3 root system into a file on an SMB network drive, then thereafter, always boot from a CD to initially load the linux kernel into memory, but have Linux mount the root from the network?

I'm thinking this might require a custom CD to be burned which would have proper linux boot parameters burned into the isolinux bootloader or something?

Can anyone provide links to documentation which could get me started on how to do such a thing?

Basically, I have a friend with a perfectly good older computer with a bad hard drive, but he also has a large NAS (2TB I think) so I was thinking we might be able to create a diskless Ubuntu system, which just boots from CD, using the NAS to store/access the filesystem?

---

### Post by snowpine on 2010-09-14
What you are describing sounds a lot like a "thin client":

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by jsbiff on 2010-09-14
Not exactly what I'm looking for. A thin client depends on another computer running the full OS, and basically you are accessing that other "terminal server" computer through the thin client. In this case, I want the computer to be just a standalone Ubuntu install that just happens to load it's root filesystem from the NAS.

Otherwise, it should be just exactly like any other 'normal' Ubuntu desktop install. Well, ok, not quite. Found out this is a really old computer with only like 128 or 256M RAM, so I probably need a really basic desktop, instead of a full Gnome setup, but that's ok too, because mostly this computer will be a web and openSSH server.

We think that in that limited capacity, this old computer should be ok - serving files which it gets off the NAS, and running some PHP scripts maybe, possibly mysql or postgres. As long as the server doesn't get slashdotted, it should be more or less ok, I think.

---

### Post by snowpine on 2010-09-14
I misunderstood; sorry for the bad link...

I haven't had great success with Ubuntu on modest hardware, but wish you the best. :)

---

### Post by oldfred on 2010-09-15
Would this be like booting the minimal CD and then chrooting into another install?

---

### Post by jsbiff on 2010-09-15
> **oldfred said:**
> Would this be like booting the minimal CD and then chrooting into another install?

Uhh, maybe, if that's necessary. I'm not really sure about what you're talking about, so if you could throw out a link, that'd be great.

Like I said, diskless server, ethernet network, want to boot from a CD (because can't boot off the network - can't do PXE, because don't have a DHCP server that supports PXE booting, or a tftp server to 'export' the necessary files for booting), then during the boot process, as early as possible, mount the root filesystem from a file available via a SMB network share, and finish booting from the network-mounted root.

This isn't absolutely required, though, as my friend can of course just get a hard drive for the machine for $30 or $50, or maybe a USB flash drive (although this computer is old enough it might not be able to boot from USB). I thought it might be an interesting challenge. Seems like it *should* be possible to do what I described.

I guess I'll spend some time reading documentation about the low level steps involved in the boot process, and see if I can figure something out.

---

### Post by oldfred on 2010-09-15
Some ISOs do not boot and the multibootUSB script copies athe kernel & init to make them bootable.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

Plop will let you boot USB from floppy
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

I guess chroot will not work, I have only used it for repairs, but it is limited.
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

---

