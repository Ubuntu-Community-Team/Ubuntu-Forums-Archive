---
title: "Run Ubuntu from USB."
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by edge2 on 2013-08-10
Hi,


I have ubuntu 9 CD. I am able to run Ubuntu OS from CD.


I want to know how to run ubuntu from USB.


-Thanks

---

### Post by mikewhatever on 2013-08-10
You write its ISO image to the USB stick with a [special tool]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows"), and reeboot.

That's about it.

---

### Post by ivan3 on 2013-08-10
Use Universal USB Installer @ [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by OrangeCrate on 2013-08-10
Another option is:

```
unetbootin
```

which is in the repositories.

Description:

> UNetbootin allows for the installation of various Linux/BSD distributions to a
partition or USB drive, so it's no different from a standard install, only it
doesn't need a CD. It can create a dual-boot install, or replace the existing
OS entirely.

---

### Post by Old_Grey_Wolf on 2013-08-10
UNetbootin can run on a Windows, Mac OS X, or Linux operating system. Their home page is [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) from where it can be downloaded.

---

### Post by Megaptera on 2013-08-11
> **edge2 said:**
> Hi, .... I have ubuntu 9 CD. I am able to run Ubuntu OS from CD. ... 

The current Long Term Support version is 12.04. Is there a particular reason you need '9' as it no longer gets updates etc.?

---

### Post by truehome on 2013-08-11
unetbootin works for other distros well for me, but for some reason it cannot put raring ringtail on a usb stick--always fails.?
Thanks, Hearthstone.

---

### Post by truehome on 2013-08-11
Whenever I use unetbootin to put live ubuntu on a usb stick, when I try to boot from it I get initramfs with the cursor flashing.
When I type "help", I get a collection of commands, but what command to use to actually boot the live ubuntu?
No such problem with other distros.
I used unetbootin to put the live ubuntu .iso on the usb stick with Linux squeeze.
Thanks, Hearthstone.

---

### Post by r_avital on 2013-08-12
Edge,

I have not tried any of the tools mentioned here, but used a procedure that worked well for me with xubuntu, kubuntu, and several versions of Mint (but did not try with straight-up ubuntu).  Might work for you.

1. Use gparted to create the partition(s) on which you want to install it, on the USB drive, and let it format to something that is supported in Ubuntu 9 (ext3, for instance).  MAke sure you also create a swap partition on the USB drive.

2. Plug the USB drive in, and reboot from your CD.  Install, and make sure that you install to the partition(s) you created previously.  For instance, in my case, I had two primary ext4 partitions and one swap.  I used one of the primariy ones for "/", the other for "/home".  Don't have the installer format the USB partitions again.  The USB partitions have to be formatted before you begin, otherwise it may not be recognized.

3. MAKE SURE that it installs a boot loader to the USB drive.

This worked quite well for me.  You shold be able to reboot from the USB drive.
Hope this helps.

EDIT:
# 3 above used to read "3. MAKE SURE that it installs a boot loader to the partition you used for "/" (root)."  That is WRONG.  My apologies.  I've corrected it above.

---

### Post by C.S.Cameron on 2013-08-12
> **edge2 said:**
> Hi,


I have ubuntu 9 CD. I am able to run Ubuntu OS from CD.


I want to know how to run ubuntu from USB.


-Thanks


Since you have burnt the Live DVD, use Startup Disk Creator to make a persistent USB.

Or do a Full install as r_avital suggests. I would recommend disabling your internal drive first though.

---

### Post by OrangeCrate on 2013-08-14
> **truehome said:**
> unetbootin works for other distros well for me, but for some reason it cannot put raring ringtail on a usb stick--always fails.?
Thanks, Hearthstone.

I've noticed the same with Ubuntu 13.04 and 13.10, though it works fine with Xubuntu. Have used it from 13.04 and numerous times from 13.10 (probably 3 x per week on average since the development cycle on Saucy started), with no problems. Mileage always varies from user to user, I guess.

---

