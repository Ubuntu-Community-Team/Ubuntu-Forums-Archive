---
title: "Can't boot into windows after installing Linux"
date: 2018-04-05
forum: MINT
---

### Post by notasurgeon on 2018-04-05
So I have two internal hard drives, /dev/sda and /dev/sdb. Windows 8.1 is installed on sda, which I have been using for years. I decided to format and install linux on sdb, not realizing that it must have contained the EFI system partition that windows has been booting off of. So now my new linux install is working great, but I cannot get back into Windows. I tried using boot-repair, but no luck there (presumably because of the lack of an EFI partition). What's the easiest way to fix this so I can get Windows booting again?

Here's the log from boot-repair, if that helps:
[http://paste.ubuntu.com/p/TqxZdYVqQW/](http://paste.ubuntu.com/p/TqxZdYVqQW/)

---

### Post by mastablasta on 2018-04-05
can you "restore" boot loader on sda using windows disk?

---

### Post by notasurgeon on 2018-04-05
I don’t actually have a cd drive. Is that possible with usb?

---

### Post by yancek on 2018-04-05
You are going to need a windows installation or recovery CD or similar as you have apparently deleted your windows EFI partition.  I would be very surprised if it was on a different physical drive but I don't really use windows.

Your windows drive is GPT which means it must be EFI.  Your Mint install is on a drive which is not GPT and you have it installed in the older MBR mode.  Having an EFI and MBR install is always going to a problem.  You should either re-install Mint EFI (have it set to boot/enable EFI before install) but you will also need to create the windows EFI partition and it's files.  There is no way to do that from any Linux.

---

### Post by coffeecat on 2018-04-05
*Thread moved to **MINT** sub-forum.*

---

