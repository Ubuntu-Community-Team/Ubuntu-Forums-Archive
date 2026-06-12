---
title: "Black Screen with GMA HD graphics?"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by Auto Lykos on 2010-11-20
Alright, so I'm trying to run 10.10 off a USB. On one computer with a nice discrete AMD graphics card, the thing boots fine. On a Dell Latitude e6510 with Intel HD Graphics (the one that comes with a Core i7) I get to the boot screen, the initial text crawl, and then the screen blanks.

Now, I can hear the standard Ubuntu start up noise about 20 seconds later so I know everything is running, just the video driver is not. 

I can not do a CD install or anything off the hard drive, only the USB. I'm wondering if anyone knows some edit you can do at the boot menu (using tab) to revert to some graphics safe mode.

I'm new, I tried looking around support documentation, but I couldn't find anything specific?

Any thoughts?

---

### Post by sikander3786 on 2010-11-20
Editing the boot menu of the USB varies from software to software that is used to create the bootable USB.

If you know how to edit it, you can delete the words "quiet & splash" and type "nomodeset" in their place.

Or access the Ubuntu boot menu by pressing any key as the computer starts booting the USB, press F6 and select nomodeset there.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Good Luck!

---

### Post by Auto Lykos on 2010-11-20
I've been getting "no kernel image" whenever I try to run one of these commands on the boot.

I'm using PenDriveLinux if that helps.

---

### Post by sikander3786 on 2010-11-20
> **Auto Lykos said:**
> I've been getting "no kernel image" whenever I try to run one of these commands on the boot.

I'm using PenDriveLinux if that helps.
If thats the case, I think the USB drive has not been prepared successfully.

Check the integrity of downloaded image first.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is ok, try considering some other software,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or some other USB drive (if available).

---

### Post by Auto Lykos on 2010-11-21
I don't think file integrity can be the issue, it works fine on one computer but not the next.

So, I booted it on another computer and tried to configure grub from there. 

Problem is update-grub isn't working. 

I've been getting an error: cannot find a device for / (is dev mounted?)

Any ideas?

Trying mount --bind /dev /mnt/dev is giving a further error about not finding a device. There is no device.map in boot/grub either. I'm still a noob, so what to do at this point is beyond me.

---

