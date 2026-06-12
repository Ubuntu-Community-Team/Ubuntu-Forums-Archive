---
title: "Lubuntu 15.10 does not boot."
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by arthur24 on 2016-01-31
I tried installing Lubuntu for the first time (v 15.10)
When I finished installing I reboot from the correct harddisk, immediately after the splash screen with the mobo logo and bootup options I get the following error>

No such device:
68a4a84a-4cc3-4a0e-8f99-6d91b283eef2.
Entering rescue mode.

I'm now accessing lubuntu from my live dvd, because I cannot boot it from the harddisk for some reason. I tried several harddisks by the way. I also tried installing from several dvds and USB devices.

Any clues?

---

### Post by Rex Bouwense on 2016-01-31
What are your computer specifications?  
Is it UEFI equipped or BIOS? 
Is this the only Operating System on your computer?  
Did you install the GRUB to your hard or is it on the flash drive? 
Did you do a MD5Sum of your download?
You didn't give us a great deal of information to go on.

---

### Post by arthur24 on 2016-01-31
Sorry for the lack of info.

8GB ram
Intel 3570K @ 4ghz
Gefore GTX 750 TI
Its a Asrock with UEFI
It's the only operating system on the computer.
Grub is on the flash drive.
No idea what a MD5sum is, so the answer is no obviously. How would I go about doing a MD5sum?

---

### Post by grahammechanical on 2016-01-31
> Grub is on the flash drive.

Are you sure. With Grub on the flash drive it will not be possible to be load Lubuntu without the flash drive being connected. Also, if Grub's configuration files are on the flash drive and you change hard drives without updating the Grub configuration files on the flash drive you will get errors like that.

It seem that Grub cannot find the drive it is supposed to boot Linux from.

From the live session please load GParted and let it scan the hard disk partitions. And then take a screen shot of the partition layout and post it in your thread.

That will give us a better idea of the partition layout. Settle on one hard disk and what is installed on that and deal with the problems that appear.

Regards.

---

### Post by arthur24 on 2016-01-31
This is a pic from the partition table of the harddisk where Lubuntu is installed.

[http://i.imgur.com/5RVq2Q6.jpg](http://i.imgur.com/5RVq2Q6.jpg)

---

### Post by sudodus on 2016-02-02
The live system works (obviously from your screenshot). It means that we should be able to get the installed system working too :-)

Run ***md5sum*** in linux or ***md5summer*** in Windows to check that the iso file was downloaded correctly (no transfer error). See this link

[UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

-o-

Since you install Lubuntu to the whole drive, it should be rather easy to use the standard method of the installer. There might be a problem with some driver. You can try with the boot option nomodeset, and after that install a proprietary driver for the nvidia graphics card. See this link

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

If still problems:

With 8 GB RAM and UEFI you should use a 64-bit system (amd64). You can try some other version of Lubuntu which might have better drivers for your hardware, 14.04.1 LTS , 14.02.2, 14.04.3 and even Xenial Xerus alpha 2 or Xenial Xerus daily. You find the development version Xenial Xerus via the following link

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

***Edit:*** Wait a minute! The screenshot of the partition table does not match UEFI. You mentioned that you run the computer in UEFI mode. If that is the case, the installer should have created a small EFI partition (with a FAT32 file system). So it seems you have installed Lubuntu in BIOS mode.

We can also ***check some things in the live system***. Please post the output of the following commands! Cut and paste the text between the web browser (and the Ubuntu Forums) and a terminal window  and back to the reply edit box here. Click the orange button 'Go advanced', select the output text and click the **#** icon to put it within [noparse]```
tags
```[/noparse].

```

uname -a

sudo parted -ls

sudo lsblk -fm

test -d /sys/firmware/efi && echo efi || echo bios
```

---

