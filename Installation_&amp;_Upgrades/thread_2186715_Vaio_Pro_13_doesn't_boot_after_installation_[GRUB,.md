---
title: "Vaio Pro 13 doesn't boot after installation [GRUB, UEFI trouble]"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by e3e9c236 on 2013-11-08
I just installed Ubuntu 13.10 on my new Vaio Pro 13, disabled safe mode, but used UEFI and not legacy mode.
I did an encrypted LVM installation and erased the complete SSD.
It booted just fine from USB, but after installation it doesn't boot.
[COLOR=#333333][FONT=UbuntuRegular]The Vaio failed boot screen appears.[/FONT][/COLOR]



I then tried this advice here: [http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi](http://askubuntu.com/questions/360285/13-10-on-vaio-pro-with-uefi)
sadly it fails for me with 


> "/usr/sbin/grub-probe: error: failed to get canonical path of /cow."




I then tried mounted the encrypted partition with Nautilus and tried this: [http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb](http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb)
With /dev/sda2 and then to install GRUB to /dev/sda.
Didn't succeed and warned me that the 


> "GPT partition label contains no BIOS Boot Partition; embedding won't
> be possible"


What do i have to do, go fix GRUB and be able to boot my finished install?
[COLOR=#333333][FONT=UbuntuRegular] Here's my Boot Repair Log:[/FONT][/COLOR][http://paste.ubuntu.com/6386598/](http://paste.ubuntu.com/6386598/)


I would really appreciate any help, 
I'm so happy to finally be able to ditch my big fat Macbook Pro and use Ubuntu on my new, light Vaio Pro, if only I could fix GRUB.


best,
x

---

### Post by heir4c on 2013-11-08
Why a encrypted and LVM installation? LVM is used when you have more Hard Drives to make a partitiontabel that overlapping the Drives sizes so you can partitioned the space without concern of the size of the HD's) and when you install the Server version. For a normal Desktop install it is useless.
So reïnstall and do it now in legacy mode and the problem is gone. Install time is about 15-20 minutes.

---

### Post by e3e9c236 on 2013-11-09
thanks for the reply.
oh, i thought LVM was just a better and more modern option.

can i go back to UEFI, if i figure out how to completely fix it?
or would i have to reinstall, after i install ubuntu with an encrypted legacy installation?

edit: just tried boot repair again, as i previously had legacy mode enabled, after the installation: [http://paste.ubuntu.com/6386598/](http://paste.ubuntu.com/6386598/)

---

### Post by fantab on 2013-11-09
From GPT SSD Ubuntu can boot in either 'UEFI' or 'Legacy' mode. If I were you I would go with UEFI. 
To boot Ubuntu in UEFI mode it needs to installed in UEFI mode and to do so the Uubntu installer MUST also boot in UEFI mode. Your SSD is ready for UEFI boot as such you just need to install ubuntu in UEFI mode.

However if you insist on 'Legacy' mode then you will have create 5mb partition (unformatted, no filesystem) and put 'bios-grub' flag on it. 

Not sure how LVM behaves with UEFI, but Ext4 filesystem works great.

Re-install Ubuntu...

---

