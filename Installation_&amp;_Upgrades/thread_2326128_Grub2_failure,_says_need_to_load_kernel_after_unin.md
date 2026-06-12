---
title: "Grub2 failure, says need to load kernel after uninstalling ubuntu 16.04"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by aaron129 on 2016-05-28
So three days ago I decided to try ubuntu again (had ubuntu 10.04 several years ago and loved it) and a bit foolishly I did a install of Ubuntu 16.04 without testing it. It became pretty obvious that the install was somehow corrupted (the network manager could not be found with any command prompts and wireless was never recognized) so I deleted the Ubuntu partitions so I could reinstall. Well I must have missed at least a part of grub because now everytime I try to start my computer it leads me to 

```
GNU GRUB version 2.02 beta2-36ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> 
```

Grub does appear to be trying to draw the necessary files from hd02 but as these were deleted it has no success

I do have a rescue usb for windows 8.1 but no dvd, a rescue disk for grub, and a live cd for ubuntu 16.04 but none of the threads I have found have been able to help. The closest I have come is the grub rescue disk which got me to windows bios but even though I set the boot order to boot the usb first it seems grub is overwriting the windows command.

The only commands that grub accepts are

```
 ls
boot
ls cd0
ls hd0,bgmt2
etc for the ls 
```

for the boot code it gives the following error message
```
 grub> boot usb
error: you need to load the kernel first 
```

If I have the repair cd in I will get the following errors before it boots to grub
```

error: failure reading sector 0x4ca5a from 'cd0'
error: failure reading sector 0x4ca20 from 'cd0'
```

I have read what seems like a hundred threads at this point and nothing seems to be working. Any help would be greatly appreciated.

---

### Post by yancek on 2016-05-28
Grub can't boot because you deleted the Ubuntu partition and almost all the Grub code was on that partition.
You mention windows 8.1, so you had it installed along with Ubuntu, correct?  Were they both installed using UEFI or MBR?  Are you planning to install Ubuntu again?  You might try using the Ubuntu DVD to run the boot repair software from the link below and post a link to the output so we have some idea of your setup.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by aaron129 on 2016-05-28
Yeah, I had meant to delete all of it but (points to first post) I missed some. :)

I  actually have no idea if they were UEFI or MBR but I would guess UEFI. I  was going to reinstall but after all this with grub I am going to have  to do a little more research before I do.

I have actually already  tried launching both the boot-repair cd and the repair through the  ubuntu live cd. Have tried 64 bit and 32 bit as I thought maybe I had  used the 32bit version but no luck.

For the boot-repair usb grub gives the message

```

grub> boot usb
error: you need to load the kernel first
```

for the second option for the boot-repair I can't get into ubuntu so I can't use it and grub doesn't recognize sudo (tried it out of desperation).


For the live cd it is the same as the usb, says I need to upload the kernel.


At this point I think I am looking at connecting from another pc and using that to fix it but I have never tried that before.

---

### Post by yancek on 2016-05-28
If you have a windows system 8.0 or later pre-installed, it is almost certainly using UEFI.  Ubuntu documentation on dual-booting with UEFI at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by aaron129 on 2016-05-28
Thank you. That will help a lot when I reinstall Ubuntu.

I didn't  see anything for the current issue (getting the recovery usb to load or  the ubuntu live cd to load from grub) but if I missed it please let me  know but once I can get either Ubuntu or Windows to load that should  help be narrow down what the problem is.

---

### Post by kansasnoob on 2016-05-28
> getting the recovery usb to load or the ubuntu live cd to load from grub

I think that grub screen has nothing to do with booting the live DVD/USB. You probably need to either adjust the settings in BIOS to boot from USB or DVD, or if this is a UEFI system then you may just need to press a key (or key combo) while booting to display the UEFI boot menu - F11 and F12 are common keys to dispaly a UEFI boot menu.

---

### Post by aaron129 on 2016-05-28
f2 is my key but the only time I have gotten it to boot to bios was once  with the grub repair disk but the boot order was already set to boot a  usb first. Somehow grub is actually stopping me from going into bios and  stopping bios from booting the usb automatically.

---

### Post by oldfred on 2016-05-28
New UEFI systems have a fast boot setting. That is different than Windows fast start setting.
It then is not grub that is preventing you from pressing a key but your UEFI.
With fast boot it assumes all system hardware and settings do not change, which often is the case. But it is so quick you do not have time to press a key. F2 may be to get into UEFI, but you also should have a one time boot key often f10 or f12, check your manual.
Windows requires the fast boot (in addition to its fast start up) so you think Windows boots faster, but it does not really.

Windows then assumes if you need to get into UEFI, you just do that from Windows. I guess they think Windows always works.

Most will give you time to press a key with a cold boot, not a warm reboot.
You need to totally power down, remove battery if laptop, hold power switch for 10 sec or so.
Then as soon as you boot press correct key(s) to get into UEFI settings or one time boot key.

Some have a tiny pin hole reset switch on bottom of system, and some only work if you jumper pins on mother board or remove coin battery on motherboard. That resets all UEFI settings to defaults so you have to reset them again.

---

### Post by djchandler on 2016-05-29
> **oldfred said:**
>  ...you think Windows boots faster, but it does not really....

Correct.

"Shutdown" in Win 10 actually hibernates your windows session. Use "Reboot," to force Windows 10 to shut down like Windows 7. This also makes Windows wipe RAM. Using Win 10's "Reboot" releases your NTFS partition for access from Linux. Otherwise, you get an error dialog when attempting to access your Win 10 partition if you "Shutdown" Win 10 and have "fast boot" in Windows enabled (default setting).

---

