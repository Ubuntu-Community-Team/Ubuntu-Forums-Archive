---
title: "Ubuntu update grub loader question"
date: 2016-06-24
forum: Installation &amp; Upgrades
---

### Post by drm200 on 2016-06-24
I have a laptop that Windows is installed on.  I installed Ubuntu 14.04 on a USB drive (using Yumi).  The laptop is setup to boot from USB.  So on start up, it defaults to Ubuntu unless I manually select windows.  I've been running this configuration for two years.  The Ubuntu updates have never been a problem.

Now,  I am just updating a ubuntu security update.  Part of the update is a grub-pc update.  During the update, I received a popup window : Configuring Grub PC.   And then it lists 3 "grup install devices" with checkboxes to be selected.  The 3 are:

dev/sda (my 500 GB laptop drive)
dev/sdb (my USB device that I have Ubuntu loaded on)
dev/sdb1 (I believe this is a USB device that I sometimes insert and boot from ... this device is not currently inserted)

I'm stuck at this point of the update, because I do not know what am I suppose to do.  Am I to select all 3 check boxes?  I would guess that I should only select device dev/sdb but am unsure and do not want to mess up my system..

---

### Post by drm200 on 2016-06-24
Ok, I have figured out what seems to work ... 

I ran this command to find where grub was: df | grep /$    which returns dev/sdb1.      

Since that USB is not installed, I selected nothing and then clicked "Forward".    

On the next Window I was asked if I want to continue to install grub.  Since the USB with grub was not insertedI chose to continue without installing grub.Seems to work fine.

I found help here: [http://askubuntu.com/questions/23418/what-do-i-select-for-grub-install-devices-after-an-update](http://askubuntu.com/questions/23418/what-do-i-select-for-grub-install-devices-after-an-update)

---

