---
title: "Questions about Ubuntu on a Flash Drive"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by jonathan97 on 2015-09-30
I'm kinda new to Linux and Ubuntu.  Recently I installed Ubuntu and my flash drive as a bootable device using UUI.  All works well, but I just have a few questions

After I installed Ubuntu on my flash drive, the flash drive renamed itself "Install Ubuntu" with the ubuntu symbol instead of the flash drive icon.  When I tried to rename it, it wouldn't let me.  Is there any way to get rid of this, since I use this flash drive as a personal one too.

One more question: Is it safe to put all the folders installed from UUI into a separate folder?  Like I said before, I use the flash drive for documents and stuff, and all the Ubuntu files just makes it look cluttered.

---

### Post by Bucky Ball on 2015-09-30
*Thread moved to **Installation & Upgrades**.*

Welcome. You can't use the USB for both an installer/persistence install and to keep your data files outside of the install (just using the USB like any regular USB). Also, any changes you make to a live USB will not stick (if you put files in folders in the live boot they will not be there when you reboot, same with adding drivers, etc. Any changes ...). 

I think you are after a [persistence]("https://help.ubuntu.com/community/LiveCD/Persistence") install. I think Universal USB Installer will create one of these fairly easily.

---

### Post by jonathan97 on 2015-09-30
> **Bucky Ball said:**
> Welcome. You can't use the USB for both an installer/persistence install and to keep your data files outside of the install (just using the USB like any regular USB). Also, any changes you make to a live USB will not stick (if you put files in folders in the live boot they will not be there when you reboot, same with adding drivers, etc. Any changes ...). 

I think you are after a [persistence]("https://help.ubuntu.com/community/LiveCD/Persistence") install. I think Universal USB Installer will create one of these fairly easily.


Oops, my bad.  I meant to say it's a persistent usb.

---

### Post by yancek on 2015-09-30
> One more question: Is it safe to put all the folders installed from UUI into a separate folder?  

No, not if you want to boot it again.  The operating system needs the files to be where they are placed during the creation of the bootable medium.  If you want to use it also for data you would need to create a separate partition.  If you want to use it between windows and Ubuntu, understand that windows will only see the first partition on a flash drive.

---

