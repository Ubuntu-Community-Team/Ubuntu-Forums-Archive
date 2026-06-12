---
title: "Can't boot into ubuntu after dual booting with Windows 8.1"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by ankit28 on 2016-02-29
Hello, i am a newbie and i just dual booted ubuntu 15.04 on a laptop with preinstalled Windows 8.1 on it, following this guide [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Now i am having the same problem as told in the guide, that my laptop will automatically boot into windows. I followed the instructions there to boot into ubuntu using the live usb and them running the commands. But my problem is, i can't connect to my wifi and the commands seem to download some tool via the internet.
So how connect to wifi, and fix this?

---

### Post by yancek on 2016-02-29
Reviewing the link you posted, the person who posted suggests that you leave the default for bootloader installation at "/dev/sda" which is incorrect if you are using UEFI which is default for windows 8 and newer.    No code is needed in the MBR if you are using UEFI and in fact, the new system won't boot which you have seen.  That is why he needed boot repair.

Boot repair is software you can put on a CD and boot from.  You can download it from the link below and burn it as a bootable image to a CD on windows with whatever burning software windows uses.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would suggest you read the link below on dual-booting Ubuntu and windows with UEFI.  You can use Disk management in windows to check to see if you have an EFI partition or probably look under My Computer which shows partitions to verify whether it is being used. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-02-29
@yancek & OP

With UEFI install default in grub2 install location is still the drive or sda. With UEFI it knows that it installs UEFI boot files to ESP - efi system partition which is the FAT32 formatted partition with boot flag.
In fact with UEFI, it does not matter whatever you select. With Ubuntu's version of grub it always installs to the ESP on sda. 

Boot-Repair does need Internet to download new packages and update system. 

Can you connect with hardwired Ethernet. That almost always works, and often then downloads a correct wi-fi driver. I guess there are too many varieties or configurations of wi-fi to include all on live installer. Some do require extra work arounds to get wi-fi to work, but that should be a separate thread.

---

