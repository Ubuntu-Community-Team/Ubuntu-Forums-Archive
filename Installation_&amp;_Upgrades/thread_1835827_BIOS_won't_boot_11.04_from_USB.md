---
title: "BIOS won't boot 11.04 from USB"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by roger_reject on 2011-08-30
Hi All,

I'm currently running a nettop on which I installed 10.10.  Not sure if I want to upgrade to 11.04 so I wanted to try it out on a USB stick for a while.  So I used the Startup Disk Creator to make a bootable disk of 11.04 following the instructions on ubuntu.org.  I've done this with several USB sticks from several different manufacturers and tried plugging them in to every one of the USB slots on the computer.  I've also tried booting into 11.04 from other computers using the same disks without any problem.

BIOS settings are set to boot from USB first, and the BIOS states that it recognizes the disk as present, but never boots from it.  If I disable booting from hard disk, it just constantly asks me to insert bootable media and press any key.

I should mention that I initially installed 10.10 from USB, so I know the computer is capable of booting from USB.  The only difference is that I used Windows to create the original 10.10 boot disk, and Ubuntu to create the new 11.04 boot disks.

Any idea what is happening or how to fix it?  I would really like to get a chance to test 11.04 on this hardware before upgrading.

Thanks!

---

### Post by roger_reject on 2011-08-30
anyone?  as some additional information i made the original 10.10 bootdisk with the universal usb installer.

---

### Post by oldfred on 2011-08-30
I do not know what version these bugs apply to:
Bugs in usb-creator unetbootin is an alternative if usb-create does not work
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by kyletstrand on 2011-08-30
I had the same issue a few weeks ago.  I had it set to USB first, but never worked.  After tinkering around with BIOS, I actually found my USB drive under the hard drives.  I changed the priority of drives to boot and had success after that.

So check that out.  Not sure if it'll be any help, but it might stir some other thought process of how to approach the issue :)

---

### Post by roger_reject on 2011-08-31
@kyletstrand,

this was the problem.  i feel like an idiot because as soon as you mentioned it i remembered having to do the exact same thing the first time i installed ubuntu.  thanks!

---

