---
title: "Problem creating bootable USB"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by BilleeSugger on 2010-12-15
I am trying to create a bootable USB of Linux . I have followed this [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) but when I try to boot from it I get Could not find kernal :Linux .
I have tried from **Make sure the partition is active**................. "Now you’ll need to run this command to figure out the number of your flash drive:.............list disk" But the command is not recognised.  I am using Windows 7 rather than Vista if that helps
Any help appreciated . I'm in uncharted water for me so please keep it as simple as possible

---

### Post by wilee-nilee on 2010-12-15
> **BilleeSugger said:**
> I am trying to create a bootable USB of Linux . I have followed this [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) but when I try to boot from it I get Could not find kernal :Linux .
I have tried from **Make sure the partition is active**................. "Now you&#8217;ll need to run this command to figure out the number of your flash drive:.............list disk" But the command is not recognised.  I am using Windows 7 rather than Vista if that helps
Any help appreciated . I'm in uncharted water for me so please keep it as simple as possible

What are you loading to the thumb? I believe unetbootin puts a boot flag on the partition.

---

### Post by BilleeSugger on 2010-12-15
Sorry, Ubuntu Ubuntu 10.10 . Don't know what you mean by bootflag

---

### Post by wilee-nilee on 2010-12-15
> **BilleeSugger said:**
> Sorry, Ubuntu Ubuntu 10.10 . Don't know what you mean by bootflag

You don't have to make the thumb active it should work if loaded correctly. Here is what a boot flag is notice it is on the W7 ntfs partition,the bootflag is what makes a partition active. This is gparted the Ubuntu partitioner.
[ATTACH]178492[/ATTACH]

---

### Post by BilleeSugger on 2010-12-15
I loaded it as shown in the link I posted . In Computer in Windows it shows the ubuntu icon beside the thumb drive. Sorry but I did ask to keep it simple

---

### Post by wilee-nilee on 2010-12-15
> **BilleeSugger said:**
> I loaded it as shown in the link I posted . In Computer in Windows it shows the ubuntu icon beside the thumb drive. Sorry but I did ask to keep it simple

So are you trying to install inside of windows or boot the thumb and have a dual boot with separate partitions?

I can only keep it as simple as I understand you and your information is quite mixed up, I am a open source user but I have XP and W7 I'm MS versed.

---

### Post by BilleeSugger on 2010-12-15
I've been trying to fix a mates laptop. It has a BSOD problem which won't allow it to boot, it won't boot from a disc either. I just had the idea that I could boot from the thumb & just leave it in the laptop so whenever the laptop was powered up it would boot into Linux on the thumb drive . He only uses Facebook, email & Youtube.

---

### Post by wilee-nilee on 2010-12-15
> **BilleeSugger said:**
> I've been trying to fix a mates laptop. It has a BSOD problem which won't allow it to boot, it won't boot from a disc either. I just had the idea that I could boot from the thumb & just leave it in the laptop so whenever the laptop was powered up it would boot into Linux on the thumb drive . He only uses Facebook, email & Youtube.

A honorable pursuit, have you tried a chkdsk /f/r with the BSOD MS set up.

---

### Post by BilleeSugger on 2010-12-15
Lost me again sorry. I'm going to have to get back to this tomorrow , it's getting late. 
Thanks for your time

---

### Post by C.S.Cameron on 2010-12-16
Try Startup Disk creator from the Live CD,
Or Universal from pendrivelinux.com
Or UNetbootin

These all make bootable USB drives.
Startup Disk Creator and Universal will make Persistent drives that will save changes.

---

### Post by BilleeSugger on 2010-12-16
Thanks mate , have used Universal & he now has Ubuntu 10.10 on the pen drive & the laptop boots from it. Not a perfect solution but ....

---

