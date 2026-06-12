---
title: "How to do a multi-boot with installers and OS?"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2018-10-08
Hello.  I want to create a multi-purpose USB stick, which contains:
1. Fast booting linux OS
2. CentOS installer
3. Windows 10 installer
4. Clonezilla

I think Ubuntu server might be a good distro to use for option 1.  I've tried several tools such as YUMI and Universal USB Installer, but it seems like they simply boot from the ISO.  So when I boot Ubuntu server, it asks me to install.  How can I actually install linux onto the USB stick, so it boots directly into the OS, not the installer?

---

### Post by oldfred on 2018-10-08
I have used just  grub to create multiple boot of ISO in flash drives, both BIOS & UEFI.
Now that flash drives are larger, I typically put a full install of Ubuntu on flash drive and use some space for booting ISO and data.

Fast booting on flash drive is not really possible. Writing is very slow, and reading can be improved a bit with settings. I did find having an SSD on a USB3 port was almost as fast as my internal SSD. But you do not have trim function with USB connections, so need drive that has internal ways to manage trim or plug drive into system occasionally.

Server does not have a gui, so that may be an issue as you do not get the option for live mode or install.

Windows may be an issue. With flash drives lower in cost, I have a USB Windows repair flash drive and not totally complicate my Linux ISO boots.

Most of my ISO I now boot from my hard drive, but actual configuration is almost the same. Getting drive and path correct to boot using grub's loopmount is the tricky part as with my system UEFI changes drive order when flash drive is plugged in on reboot. It becomes sda and hd0 in grub.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by spookybathtub on 2018-10-08
Thanks for the reply.  I only plan on using the ubuntu system for occasional use and troubleshooting, so I won't be writing much data to the filesystem.  I only need this because the other boot utilities I've tried like gparted or clonezilla have reduced functionality in the shell and some things won't work (specifically storcli and ipmicfg)

Your links seem to be talking about booting an ISO.  I know how to boot the Ubuntu installer ISO, but that doesn't let me boot directly into a working Ubuntu system.  Are you talking about making your own custom ISO for the installed system?

---

### Post by monkeybrain20122 on 2018-10-08
multisystem creates multiboot usb for many distros and rescue cd

[http://liveusb.info/dotclear/index.php?pages/os](http://liveusb.info/dotclear/index.php?pages/os)

Not sure about windows though, usually Windows is incompatible with other things and requires different tools. I would just use a different usb.

---

### Post by wildmanne39 on 2018-10-08
*Thread moved to **Installation & Upgrades since this topic seems more of a support question then discussion**.*

---

### Post by oldfred on 2018-10-08
Are you installing to flash drive and then wanting to be able to boot an install in your system?
Install to a flash drive is like any install to a second drive. You must partition in advance.
A bit more complicated with UEFI as UEFI only boots from /EFI/Boot/bootx64.efi and grub only installs to ESP on internal drive to /EFI/ubuntu/shimx64.efi.

The os-prober will find all systems and add then to grub menu. I normally turn off os-prober and add my own boot stanzas to 40_custom.

---

### Post by C.S.Cameron on 2018-10-09
The following makes a MultiBoot USB with Multi Persistence that boots BIOS or UEFI.

[https://askubuntu.com/questions/46624/how-to-create-a-bootable-usb-with-multiple-iso-images-in-it/992857#992857](https://askubuntu.com/questions/46624/how-to-create-a-bootable-usb-with-multiple-iso-images-in-it/992857#992857)

You can also divide the drive into four partitions and use **UNetbootin** to install an OS to each, if you don't need more than 8GB, persistence on each, (casper-rw + home-rw).

(Method shown on same Ask page as mkusb hack).

---

### Post by spookybathtub on 2018-10-11
No need for EFI, I'm keeping it simple with BIOS boot.  I got stuck during the install of the first OS.  It might be a bug in the installer when installing from one USB drive to another.  Bug filed here: [https://bugs.launchpad.net/curtin/+bug/1796977](https://bugs.launchpad.net/curtin/+bug/1796977)

---

### Post by C.S.Cameron on 2018-10-11
If you use UNetbootin, (Windows), it takes care of BIOS and UEFI automatically.

---

