---
title: "Ubuntu 14.04 32-bit Live USB (longhaul: option &quot;enable&quot;)"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by alex-neblett on 2014-09-15
Using live USB to try\install Ubuntu 14.04 with no luck. I then found there was a way to do this via grub.cfg. Located boot\grub\loopback.cfg but I am having difficulty with command syntax. any help would greatly be appreciated.

---

### Post by dave131 on 2014-09-15
Could you clarify the following for us:

- are you wanting to create a live media on USB to actually run Ubuntu off of

-- or --

- are you trying use a live media USB to install Ubuntu to your hard disk

If you use something like unetbootin to create the USB flash drive, as long as your BIOS is set to allow booting from USB before it checks your hard disk you shouldn't have to do anything else - just boot with the USB flash plugged in.  You should get the same options to try or install Ubuntu, and the installation would be just as installing from the LiveDVD would be.

[COLOR=#0000cd][I]EDIT:  I may have missed something here given the title of the thread.  What option are you trying to enable?  If you need a boot option when just running off a Live media (USB or DVD) I believe you hold down the shift key as the system is powering up/booting and you will get the menu.  From there just "e"dit the boot you want to do and put in your option.  If the option is needed permanently (such as nomodeset) after the boot, we can tell you how to do that as well.
[/I][/COLOR]

---

### Post by oldfred on 2014-09-17
I boot ISO directly from another partition on another drive and from flash drives using grub2's loopmount.
Issues usually  are drive number and path. Drive will always be hd0 if grub is in same drive, but drive number can be just about anything if you boot from one drive and ISO are on anther drive. I had to experiment.
Path is as seen before you mount a partition as grub has not loaded Ubuntu and its default mounts.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)


 Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

There are also many scripts now that will create a flash drive with many ISO for booting. Some use other boot loaders.
      
 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)

---

