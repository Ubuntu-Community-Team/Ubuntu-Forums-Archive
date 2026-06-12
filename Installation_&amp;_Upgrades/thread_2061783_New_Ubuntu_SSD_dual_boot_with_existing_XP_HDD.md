---
title: "New Ubuntu SSD dual boot with existing XP HDD"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by morticiaskeeper on 2012-09-23
Sorry if I've missed something in my searches :-(

I've had a dual boot system for some time, with 12.04 on a SATA drive and WinXP on an IDE drive.  Grub looked after dual booting with no problems.

After a few problems with the Ubuntu install, probably caused by me trying to free up disk space, I installed 12.04 on a new SATA SSD.

The existing SATA drive is working as media storage and the IDE WinXP drive is fully readable from the new install.

How do I now go about setting up a dual boot menu?  I'm a bit nervous about killing either install, although if I have to, rebuilding the 12.04 side would be the easier of the two.

Cheers

Paul

---

### Post by darkod on 2012-09-23
So, what is the question exactly? You say you already installed 12.04. If the XP disk was connected during the install it should have detected it and you should already have a dual boot grub menu when you boot.

But with three disks make sure you are booting from the correct disk where the latest grub is. Sometimes it can be installed not on the same disk as 12.04 but on the disk that was first in boot order.

That's why I always recommend doing manual installs, not automatic ones, because you have control where the bootloader goes, among other things.

Try changing the disk boot order to see if there is grub on another disk, and if that is not some older grub install from earlier. If you manage to find the grub on another disk, you can boot ubuntu once and install grub to what ever disk you want.

You can also do it with the 12.04 cd in live mode, if there doesn't seem to be a working grub on any disk.

---

### Post by morticiaskeeper on 2012-09-23
No other drives were connected when the 12.04 install went on. I was having a few problems getting the pc to boot from the correct drive, the BIOS boot order was USB/USB/USB, yet it still tried to boot from a HDD. so I unplugged all drives, booted from USB into a live session, plugged in the SATA SSD then plugged in the other drives when everything was installed.

I have found another menu in the BIOS which should give me a guaranteed boot from the USB stick.  Would it be better if I start again?  I've got good backups and it's all fresh in my mind.  I'd rather do it now then in a few weeks!

Paul

---

### Post by darkod on 2012-09-23
No, it should be good. In that case grub2 might be on the usb stick since that is what you booted from.

But what do you mean "you connected the ssd"? You can't connect disks while the computer is on, usually they are not hot-plug like on servers. If you did that I hope nothing got fried.

Try booting from the ssd because it was the only disk when installing. If that doesn't work, try booting with the usb connected in case grub2 ended up there.

If it works with the usb, open terminal and check the ssd device name with:
sudo fdisk -l (small L)

Then when you know which device is the ssd, install grub2 there with:
sudo grub-install /dev/sdX

using the correct device name instead of sdX.

After that reboot without the usb, with the ssd as first option, and it should work.

When you get ubuntu running without problems, to add XP to the boot menu run:
sudo update-grub

---

### Post by morticiaskeeper on 2012-09-23
Grub was on the SSD :KS

I hot plugged the signal on the SATA drive, but wouldn't do it with power or IDE drives.

Thanks for your help.

Paul

---

