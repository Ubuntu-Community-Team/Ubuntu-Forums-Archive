---
title: "Installation of Ubuntu GUI  on a USB drive"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by sudtech on 2012-10-17
Can Ubuntu be installed in an USB pendrive of 8GB and booted to a GUI mode . Are there any images available for the same .

---

### Post by PowerBarry43 on 2012-10-17
Hi

Sorry I don't have any images for you but I've done this successfully on a USB external hard drive and the procedure is the same as installing to any other device you just need to make sure that you install the boatloader to the USB drive. I would recommend disconnecting your internal hard drive(s) if you can. Although this is not essential, it makes it much less likely for you to accidentally wipe your hard drive!

Hope this helps!

Barry

---

### Post by jerrrys on 2012-10-17
Persistence install, here's a few of ways to do it

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by PowerBarry43 on 2012-10-17
as jerrrys says there are other ways, it depends whether you want it to be a liveUSB which you can install from or a full installed distro

Barry

---

### Post by oldfred on 2012-10-17
Persistent installs are the standard installer with some space to store your data. Better for 4GB or smaller flash drives, but can be used on larger ones.

Full installs work fine from 8GB or larger. 

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

I have a full install of Ubuntu on a 16GB flash in a 8GB partition with 8GB for data. You will want to make some settings similar to a SSD to reduce writes, but otherwise it is like any install to a second drive or external drive.

Some suggest Lubuntu as the lighterweight applications load a bit faster. But if you have 4GB of RAM or more once apps load they are in RAM and it works reasonably well.

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by sudtech on 2012-10-18
Dear All

Thanks for the replies , i will check the same with regards to the persistent and liveusb formats .

---

### Post by sudtech on 2012-10-18
In continuation with the thread on Linux Installation on USB drive , pl let me know if anyone knows about the boot options from USB drive .

Newer Motherboards BIOS  have the option ,what about if i use an older motherboard ,does it have an option or do i need to upgrade the BIOS or any patches available for the same .

---

### Post by Cheesemill on 2012-10-18
***Some*** older motherboards may let you update the BIOS to allow booting from USB, with others it's just not possible.

One option for motherboards that don't support booting directly from USB is to use a boot loader such as [PLOP Boot Manager]("http://www.plop.at/en/bootmanagers.html"). This will let you boot from a CD/floppy which then loads the USB drivers and lets you select your USB drive to boot from.

---

