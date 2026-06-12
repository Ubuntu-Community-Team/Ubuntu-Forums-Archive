---
title: "Installer cannot see eMMC drive on HP Stream laptop"
date: 2021-12-07
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2021-12-07
Hi, I am currently running US 20.04 on my HP Stream laptop and dual booting with Win10. I was able to install US on a SD card and created the /boot directory on the eMMC drive for dual booting purposes.

So, currently I have 

1. /dev/mmcblk0p1 - ESP
2. /dev/mmcblk0p2 - MS Reserved
3. /dev/mmcblk0p3 - Win10
4. /dev/mmcblk0p4 - Ubuntu /boot 

on the eMMC drive

and

1. /dev/mmcblk1p1 - Ubuntu /
2. /dev/mmcblk1p2 - Ubuntu /home 

on the SD card

I was trying to upgrade US from existing 20.04 to 21.10

When I boot off the LiveUSB

* I can see both drives and all the partitions
* Can mount Windows partitions and Ubuntu /boot 
* all partitions are mounted with rw access.

However, when I run the installer, it fails to recognise the eMMC drive and none of the partitions are listed when manual partition selection option is chosen.

I could continue with installing on the SD card, copy the new boot files to /boot directory in the eMMC drive and update grub which will get me going but curious to find out the reason why the installer cannot detect the eMMC drive. I also tested with a Lubuntu 20.04 LiveUSB (which appear to use the same installer) and exact same problem is found in that case too.

Thanks

---

### Post by tea for one on 2021-12-08
A couple of guesses:-

Windows update turned on hibernation and the Calamares installer cannot find /dev/mmcblk0

The Calamares installer does not automatically display all the storage devices on one page
Partitions > Storage Device (at top of page) > Click Down Arrow > Displays one or more target devices

Tested with Lubuntu Installer 21.04 on a HPStream 2016 model (No Windows OS replaced by Xubuntu (with Ext4) on the internal /dev/mmcblk0)

---

### Post by gdesilva on 2021-12-08
> **tea for one said:**
> 
Windows update turned on hibernation and the Calamares installer cannot find /dev/mmcblk0


I actually turned off hibernation on Windows by running powercfg.exe /H off command. Now I do not get the sleep option on Windows which is indicative that hibernation is completely turned off. Again, what I cannot understand is that if I am able to manually mount any of the partitions of mmcblk0 and if partition manager can see all the partitions yet why is that the installer cannot see it? At this stage it seem to point to an issue with the installer?

> **tea for one said:**
> 
The Calamares installer does not automatically display all the storage devices on one page
Partitions > Storage Device (at top of page) > Click Down Arrow > Displays one or more target devices


Tried many times but the drop down menu only shows the mmcblk1 which is rather weird. Strange, when I tried the Lubuntu 20.04 LiveUSB, I get the same result as with the US 21.04 LiveUSB.

Thanks very much for your comments.

---

### Post by tea for one on 2021-12-08
Yes, it is unusual behaviour when the installer fails to recognise your internal /dev/mmcblk0.

Out of curiosity, if you have time, can you try the following experiment:-

Shut down Ubuntu
Power off PC
Remove the micro SD card from the card reader
Boot into a live session with your Lubuntu 20.04 ISO
Start the installer to see if the internal mmcblk0 is available

---

### Post by gdesilva on 2021-12-08
I did remove the micro SD card and tried the installer a couple of days ago, and then it says there are no devices to install the system.

---

### Post by tea for one on 2021-12-09
Not making much progress yet, but, let's crack on with some more suggestions.
How about downloading another ISO with a different installer e.g Xubuntu?

Edit: Not to install Xubuntu, just to see if the internal storage is recognised

---

### Post by gdesilva on 2021-12-09
@tea for one, thanks for the suggestion. Yes, Xubuntu 21.04 installer does detect both mmcblk0 and mmcblk1 and I can choose any of the partitions now. This confirms my initial hunch that it is an issue with the installer as I had no problem mounting the partitions but installer could not see them.


EDIT: I rebooted with Ubuntu Studio 21.10 and ran calamares with -d (debug) option on a terminal ([https://pastebin.com/W8ds0NYt](https://pastebin.com/W8ds0NYt)). The output specifically says that it is removing mmcblk0 (the eMMC drive) from the list as it thinks it is possibly a CD. This explains why it does not appear on the list of installable devices. Any ideas on how to make it appear as a non-CD drive?

---

### Post by tea for one on 2021-12-10
That's a step in the right direction - especially running Calamares in de-bug mode. I would never have thought of that.

Regrettably, I do not know how to make /dev/mmcblk0 appear as a non-CD drive.

However, when you look at the de-bug info 
```
Line 277 - Removing device with iso9660 filesystem (probably a CD) on it "/dev/mmcblk0" 
Line 278 - Removing device with iso9660 filesystem (probably a CD) on it "/dev/sda"

```

Device sda is probably your live session usb stick and should be excluded because it has a valid iso9660 filesystem.
Why is /dev/mmcblk0 reporting a iso9660 filesystem also?

Perhaps have a search through your internal storage to see if there is a match?
I don't know how Windows utilities would do this (perhaps ask in a Windows 10 forum)?

---

### Post by gdesilva on 2021-12-11
> **tea for one said:**
> 

Perhaps have a search through your internal storage to see if there is a match?


I am fairly confident that this is a bug in calamares as I have no problems mounting any of the mmcblk0 partitions and writing/deleting files when the booted with the LiveUSB. Problem occurs only when calamares tries to identify editable partitions and it just assumes that mmcblk0 is a read only device.

If you think of any other ideas, please let me know. Thanks.

---

