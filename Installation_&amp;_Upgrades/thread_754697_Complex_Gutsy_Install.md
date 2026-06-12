---
title: "Complex Gutsy Install"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by sslk on 2008-04-14
Heres my complicated situation. I have been all over the internet and especially this forum,and haven't found answers that work, so I'm guessing this install question is unique.

Background: I want to install Ubuntu 7.10 on my relatively new  laptop. This laptop was originally loaded with vista home premium, but it doesn't make a difference whether or not vista is usable. I previously installed gutsy on this laptop without any unusual issues, however after a hard drive failure and replacement I find that I can no longer boot from the CD drive (with apparently the exception of the hp vista recovery disk). Yes, I've checked all motherboard related issues (BIOS is up to date, boot options are properly set), and the drive itself (although vista recognizes all cds/dvds as blank, other apps such as VLC media player recognize content appropriately), and I've checked the hard drive for any issues which could relate to installation (I can install / use the laptop hard drive in my desktop perfectly).

So, i'm left without the ability to boot from cd.

I've installed 7.10 onto the laptop hard drive while it (the laptop HD) is inside of the desktop. When placed back into the laptop the Grub loader properly recognizes the new installation (along with memtest and recovery), but when it tries to boot the OS it get stuck in its scipts before hardware drivers are loaded.

I've also tried to make a USB flash disk bootable and install onto the laptop hard drive, but failed in getting the flash disk to boot. While waiting for replies I will attempt that again anyway. I do not have a USB cd drive or USB floppy.

Any suggestions on how to install Ubuntu on my laptop?

Thanks in advance

---

### Post by Jussi Kukkonen on 2008-04-14
You can try netboot if you have another linux machine and the laptop BIOS supports it (may be called PXE or network boot).

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by warp99 on 2008-04-14
> **sslk said:**
> When placed back into the laptop the Grub loader properly recognizes the new installation (along with memtest and recovery), but when it tries to boot the OS it get stuck in its scipts before hardware drivers are loaded.

What scripts are you taking about? Can you boot into recovery mode on this computer? There is no need to reinstall the OS since you can take the drive out of one machine and install it into a different one without problems except maybe setting the graphics drivers, which takes about 30 seconds.

---

### Post by sslk on 2008-04-16
The scripts I mentioned were the 4-5 lines of code right before:

* Running local boot scripts (/etc/rc.local)


The problem is seemingly FIXED through the following process...
1. HP recovery cd restores laptop to factory condition
2. Use the procedure detailed on pendrivelinux . com to install Hardy beta on the laptop, using umenu to help me install without being able to boot from CD.

Although pendrivelinux . com didn't have a solution a few days a go when the problem originally appeared, the solution appeared while i was looking for a way to boot knoppix via usb on an older laptop.

Thanks for the interest anyway, warp99 and jussi kukkonen.

---

### Post by warp99 on 2008-04-16
> **sslk said:**
> The scripts I mentioned were the 4-5 lines of code right before:

* Running local boot scripts (/etc/rc.local)


The problem is seemingly FIXED through the following process...
1. HP recovery cd restores laptop to factory condition
2. Use the procedure detailed on pendrivelinux . com to install Hardy beta on the laptop, using umenu to help me install without being able to boot from CD.

Although pendrivelinux . com didn't have a solution a few days a go when the problem originally appeared, the solution appeared while i was looking for a way to boot knoppix via usb on an older laptop.

Thanks for the interest anyway, warp99 and jussi kukkonen.

Well next time if you need to boot to a CD you can use Gujin bootloader, then chainload the CD:

[http://gujin.sourceforge.net/](http://gujin.sourceforge.net/)

[http://sourceforge.net/projects/gujin/](http://sourceforge.net/projects/gujin/)

Stick it on a usb or sd flash. You can even use a floppy. It also allows you to boot directly to an ISO.

---

