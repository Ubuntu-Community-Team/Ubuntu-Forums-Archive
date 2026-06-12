---
title: "Booting from external USB drive"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by bamarob on 2006-06-22
Hello all.  I've been using Ubuntu on several desktops and one laptop since Hoary.  Been a Debian user for much longer.  Anyhow, this has me stumped and I'd like some help.

I've successfully installed Ubuntu 6.06 LTS to a 40 GB external USB drive.  But when I go to boot from it on my laptop, it gets to the 'Uncompressing Linux... OK Booting kernel', then switches to the graphic boot screen.  On this screen, at the bottom I see:

Loading essential drivers...
Mounting root file system...
Waiting for root file system...

Then it just sits there.  If I hit CTRL-F1, I still see the 'Uncompressing Linux... OK Booting kernel' messasge.  If I hit CTRL-F8, I see:

udevd-event[1888]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.4/1-6.4:1.0/host0/target0:0:0/0:0:0:0/bus' failed

I can then unplug the external USB drive and plug it back in and it continues the boot process and boots fine.  I'm posting this from firefox running on Ubuntu running on the USB drive right at this very moment. :D

I looked at the thread here: [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811) as it seemed to address a similar problem (though with Breezy rather than Dapper).  I followed the directions there and have edited my '/etc/mkinitramfs/modules' to include:

ehci_hcd
uhci_hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod

and, rebuilt my initrd.img using:

mkinitramfs -o /boot/initrd.img-2.6.15-23-386 /lib/modules/2.6.16-23-386

I checked to make sure everything was right with grub's menu.lst.

Any suggestions would be greatly appreciated.

Thanks,

BR

---

