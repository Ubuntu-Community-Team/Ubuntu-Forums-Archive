---
title: "GRUB menuentry to boot iso file from USB stick?"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by 1204 on 2012-10-09
Well, is it possible? I have GRUB on my harddrive and usb stick won't boot, I've tried everything. ubuntu-12.04.1-desktop-amd64.iso

SOLVE:
[http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot](http://www.linuxjournal.com/content/using-plop-boot-manager-usb-boot)
[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

---

### Post by davidbilla on 2012-10-09
USB boot is something that you choose at your BIOS during bootup. If you have created a proper startup disk from the ubuntu iso, your system should boot from the USB.

Is that what you wanted or am I mistaken?

---

### Post by oldfred on 2012-10-09
You select in BIOS to boot the USB flash drive, if you installed in any of the standard ways. If BIOS does not give an option to boot USB port then you may be able to use plop boot loader.

You can copy the ISO (not a normal install) to a partition and use grub to loop mount the ISO file directly. Does not work with all ISOs. But BIOS still has to support booting from flash drive.

These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

---

### Post by 1204 on 2012-10-09
I have grub on my hard drive and I can get to it by pressing shift. Let's say *ubuntu.iso* is on my USB stick. Can I write a menuentry to */boot/grub/grub.cfg *on my hard drive*,* that mounts USB drive and reads ubuntu.iso?
> **davidbilla said:**
> USB boot is something that you choose at your BIOS during bootup. If you have created a proper startup disk from the ubuntu iso, your system should boot from the USB.

Is that what you wanted or am I mistaken?But my system don't boot from usb stick, I've tried every BIOS setting. Other machine boots so it's not about usb but my system. Optical drive is broken, which I used before, so it is not an option. :)

---

### Post by oldfred on 2012-10-09
If BIOS will not let you boot from flash drive on USB port then grub will not boot it. 

How old is computer? Both of mine are about 6 years old and boot from USB flash drives. I was lucky as that was about the time most systems changed BIOS to allow USB boot.  On one it has many USB boot choices and none of them boot a flash drive. But when I choose which hard drive to boot, then the flash drive is an option. Flash does have to be bootable for it to appear in hard drive menu.

If system is older than 6 years then it may not boot flash drives.

Some have had success using this to boot a USB flash drive when BIOS does not let them boot.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by 1204 on 2012-10-09
> **oldfred said:**
> If BIOS will not let you boot from flash drive on USB port then grub will not boot it. How old is computer?Only 4 years old, and it has boot from USB but it won't boot. I have seen couple PCs that does the same and it just don't boot whatever BIOS options you try. CD always boots, but in this case my drive is broken. :)


I think I found it, can I just put */dev/sdb1/file.iso* as usb stick usually is? [http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

```
menuentry "**Lucid ISO**" {
set isofile="/boot/iso/ubuntu-10.04-desktop-i386.iso"
loopback loop (hd0,1)[COLOR=Navy]$isofile
[/COLOR]linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=[COLOR=Navy]$isofile[/COLOR] noprompt noeject
initrd (loop)/casper/initrd.lz
}                      
```

---

### Post by 1204 on 2012-10-09
I have Ubuntu 12.04 at the moment.
I have upgraded it 10.04-10.10-11.04-11.10-12.04...
It means my system is bloat and not only because I have tested all kinds of things
This point it's easier to re-install than clean it
I have grub on my hard drive and it works
I would like to do GRUB menu entry to hard drive, that it loads ISO file from my USB stick so I could re-install ubuntu

It's not impossible but I don't know how. I can learn to do it but I hope someone knows already how to load iso file from usb stick:KS

---

### Post by oldfred on 2012-10-09
I use the entry you posted, but I am booting ISO from another partition on another drive so it has a slightly different path.

You have to copy the ISO not a normal install to the flash drive. Most times we are telling users to not copy ISO but use the tools to install/extract the ISO to the flash drive.

You may/should still install grub2's boot loader to the USB flash drive. 
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

You need to do this and then create a folder in the /boot folder so you have /boot/iso. Then copy the ISO to the /boot/iso folder. Update description in grub entry to exact name of ISO you are booting.
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

If you are booting from hard drive but want to use partition on USB, the grub2 boot loader will see the USB as hd1. The boot drive is always hd0. With multiple drives it can get very confusing and I often have to manually edit emnu entry to correct drive number when booting as I have several drives and may boot from any of them.

More examples, no real difference from hard drive and USB flash drive if system will boot from flash drive:
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by 1204 on 2012-10-10
Thanks guys.

---

