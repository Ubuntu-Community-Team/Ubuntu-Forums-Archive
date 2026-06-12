---
title: "Install ubuntu on desktop work on laptop?"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by allsystems on 2010-12-16
If I install a regular version of Ubuntu onto a USB drive using my desktop,can i plug the usb into my laptop and it will work normal,no issues having used the laptop desktop to install to the usb. Only reason asking because i can disable the harddrive on my laptop so i just unplug the harddrive in my desktop and install ubuntu like that onto usb,if theres a better method for laptop love to hear it

---

### Post by Dutch70 on 2010-12-16
Mind if I ask why you are "disabling & unplugging your hard drives?

All you have to do is boot from the usb if I understand you correctly.

[*_[COLOR="Red"]Check here[/COLOR]_*]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

Hope that helps.

---

### Post by Sef on 2010-12-16
You can set your BIOS to check the usb ports before booting from the hard drive. 

Another way is to press (usually) F11 or F12, and it will give you a choice of where you want to boot into from.

---

### Post by efflandt on 2010-12-17
Yes a regular Ubuntu install on USB is portable (or even on an internal drive) as long as you make sure that you put grub on mbr of that USB or drive.  However, it is best to stick with default video drivers if moving it between different computers unless they can all use those video drivers.  For 10.10 you can chose where to put grub at **bottom of manual partitioning screen**.  for 10.04 or earlier the **Advanced** button on screen after you set your user can set where to put grub.

I initially swapped out my laptop hard drive with an SSD drive and used the laptop to install Ubuntu to sda.  It was no problem moving that SSD to my desktop PC and telling its BIOS to boot from it when it was sdb.  Or if I do a regular install to USB stick, it boots fine regardless of which drive it ends up as.  That is the beauty of using UUID's instead of hard coded devices for finding and mounting partitions.

The only issue I ran across is that "some" computers cannot seem to boot if /boot/grub is too far out on a USB hard drive, but I have not figured out why.  For example my new Dell desktop can boot Ubuntu at the far end of its 1 TB internal drive or 160 GB USB drive, but not at the far end of a 500 GB USB drive.  Yet that same 500 GB USB drive boots fine on 2 different laptops (including a Dell) from 2006.  The desktop boots Ubuntu on identical 500 GB USB drive if Linux partition is closer to the beginning of the drive.

---

