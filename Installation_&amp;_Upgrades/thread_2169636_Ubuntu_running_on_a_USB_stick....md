---
title: "Ubuntu running on a USB stick...?"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by mark48 on 2013-08-22
Ok so i have loaded ubuntu 13.04 on a usb stick using the pendrive website installer.  I have downloaded the iso and it created a live version on the stick.  How can i actually run ubuntu from the stick as an actual os instead of running it as a live version?  Thank you in advance...

---

### Post by Dennis N on 2013-08-22
The short answer is that you will need a second usb stick to install the os on, using the one you have as the installer.

---

### Post by mark48 on 2013-08-22
> **Dennis N said:**
> The short answer is that you will need a second usb stick to install the os on, using the one you have as the installer.

Ok so then i also have the same iso burned to a dvd.  Can i load the live dvd and install it to the usb stick?  The usb stick is 64gigs.

---

### Post by Dennis N on 2013-08-22
Sure. You can use the dvd as the installer, and your usb stick as the place to install. 

You need to set up a partition table on the stick: choose "do something else" when asked how you want to install. That should allow you to get to the tools to set up a new partition table, and then make two partitions that you will need on your usb, one primary partition and one swap.

Once that is done, you have the installer install Ubuntu using the primary partition that you created as the root (/) partion. Caution: Be sure that you install to the correct device (usb stick) and not your hard drive by accident.

The rest is done by the the installer, with a bit of input (user name, password, location) by you.

---

### Post by Dennis N on 2013-08-22
Just to add, you need to install the boot loader to the usb stick as well, not your hard drive. This will allow you to boot from the usb.

---

### Post by mark48 on 2013-08-22
Ok, i am going to try it.  Not sure on the bootloader part but hopefully it will tell me.

---

### Post by Dennis N on 2013-08-22
Just read carefully as you go along. I think you also can get to the partition editor from running a live dvd session before you start installing. It is called gparted and should be listed in the applications.

---

### Post by mark48 on 2013-08-22
ok thank you.

---

### Post by Dennis N on 2013-08-23
@mark48: See 
[http://ubuntuforums.org/showthread.php?t=2169661&p=12766144#post12766144](http://ubuntuforums.org/showthread.php?t=2169661&p=12766144#post12766144)
for posted notes I located on this topic, with a detailed list of the steps taken.

---

### Post by hg-knight on 2013-08-23
thanks from me as well, will come in handy

---

### Post by kurt18947 on 2013-08-23
> **mark48 said:**
> Ok, i am going to try it.  Not sure on the bootloader part but hopefully it will tell me.

It's on the same screen as the partition information near the bottom.  The default is usually sda, the root of your hard drive.  You want GRUB to go on sdb (or sdc etc.)  You'll be able to tell which 'letter' is your USB drive by size.  Another aspect I found confusing is when selecting the partition to format & install you don't just click on the partition, nothing will happen.  You click 'change' then select the partition, desired format etc.  If you are using a desktop machine are are familiar with it's internals, you could unplug your hard drive, it is not required for this operation.  That way you can't mess up what you are using now.

---

### Post by sudodus on 2013-08-23
+1

Unplugging the internal drive makes things easier and safer.

I would like to add, that you should

- avoid swapping (except for rare occasions), otherwise it will wear out the flash hardware.
- add the ***noatime*** option for the root partition in [FONT=courier new]**/etc/fstab**[/FONT] for the same reason.

You can read about USB drives and speed at this link
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

