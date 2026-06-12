---
title: "14:04 won't boot from usb stick"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by James Wilde on 2016-02-17
I've installed Ubuntu 14:04.3 onto two usb sticks.  One I loaded with the dd command to load the 64 bit iso, whilst with the other I started the live CD and installed to the other usb stick.  Neither of these will boot, and I have noted from searching the forum that this appears to be a problem.  I saw the hint to use Unetbootin, but this had fastened at the bottom of the window to 'USB drive' and '/dev/disk2s1', and I wanted /dev/disk1s1, which I also couldn't change.  So out went Unetbootin, and now I'm wondering how to do this.

I thought the Ubuntu live install disk was supposed to work on any suitable medium.  That's what happens with OSX - I can test a new version of OSX by installing it to a USB stick and running it from there.

Before anybody asks, I loaded grub onto the stick.

Any clues about what I should do next?

---

### Post by sudodus on 2016-02-17
Which iso file is it (32-bit - i386 or 64-bit - amd64)?

Did you check with md5sum, that the downloaded iso file is good?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Please specify your computer! It makes it easier to give relevant halp.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Is the computer running in UEFI mode or BIOS mode?

-o-

You can try mkusb to create a USB boot drive from the iso file.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

### Post by James Wilde on 2016-02-17
Thanks for your interest, Sudodus.  It is the 64 bit iso.  I haven't checked the md5.  I seldom do, but the iso, when burnt to a DVD starts and runs with no problems.

The computer is a HP 4540s with a 2.39 GHz Intel Core i3 CPU, 8 GB ram, Intel HD Graphics 4000 1024 MB and a D-Link 11n usb connector.  I suspect it is running in UEFI mode, as EFI file is one of the boot options.

Am I supposed to run mkusb when I have booted from the live install DVD or are there versions for other OSs, as I'm not running Ubuntu other than when I use the live install DVD?

---

### Post by sudodus on 2016-02-17
The 64-bit version is good for UEFI mode. Intel graphics should work with the built-in drivers (as shown when you boot from the DVD drive). I'm no expert of wifi, but other people can help you if necessary. It is good to have a wired connection during installation (from the live system to an internal drive).

You can run mkusb from several of the main linux operating systems (including from the DVD with Ubuntu live), [mkusb, mkusb-nox and mkusb-bas](https://help.ubuntu.com/community/mkusb/gui#Simple_to_test_mkusb_in_linux_distros.2C_which_do_not_manage_an_Ubuntu_PPA).

You can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to install Ubuntu to a USB pendrive from Windows.

-o-

Read more about installing in UEFI mode at this link and links from it: [Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by James Wilde on 2016-02-17
OK Sudodus, I'm off on a three-day trip tomorrow and won't be able to try this until after the weekend.  I'll come back on this later.

---

### Post by James Wilde on 2016-02-22
OK, now I've had the chance to look into mkusb a little more thoroughly, and it's not what I want.

I have a usb stick configured, just as I would configure an ordinary hard disk, with Ubuntu the way I want it, with a / partition and a /home partition, but it won't boot.  I just want to make the usb stick bootable so that I can run Ubuntu as though it was on my hard drive and to do this I want to make the usb stick bootable.  I can do this with OSX.  I have a usb stick with 10:10 that I have run to test whether I like it or not, and I could do the same thing with 10:11.

So how do I make a non-bootable usb stick into a bootable one.  I will - reluctantly and unwillingly - accept haviing to wipe my usb stick, formatting it to be bootable, and then reinstalling ubuntu, but I'd rather just make whatever change is necessary to the mbr which will make it bootable as is.

---

### Post by sudodus on 2016-02-22
Some HP computers are a bit tricky to make bootable from USB. Sometimes it helps to add the ***boot flag*** to the partition you want to boot from.

If you have installed Ubuntu in UEFI mode, there should already be an EFI partition with a boot flag. Otherwise, if you have installed Ubuntu in BIOS mode, you can try to add a boot flag to the root partition, /. You can use gparted (when booted from another drive) to add the boot flag.

If your USB stick is installed in one mode and the computer is booting in the other mode (UEFI/BIOS), you should change either of them.

See these links for more details,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
[UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)
[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)
[Pendrive ability to boot]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221")

---

### Post by oldfred on 2016-02-22
If you installed in UEFI mode to an external drive, then you need to manually copy /EFI/ubuntu from sda's ESP to the external drive's ESP - efi system partition. And then copy again at least the /EFI/ubuntu/shimx64.efi to /EFI/Boot and rename to bootx64.efi. Version of grub with standard install is hard coded to look for /EFI/ubuntu/grub.cfg. So you must have that and the bootx64.efi that really is shimx64.efi.

If you did not create or have an ESP and gpt partitioning on external drive you need to change that.

All external UEFI devices boot from /EFI/Boot/bootx64.efi. And that also is a backup way or fallback way to boot internal devices.

You may need to have UEFI set to allow USB or external boot.

---

### Post by goofprog on 2016-02-22
To make a USB bootable OS, I usually remove all drives from the system unit and then I install it on the USB drive just like installing to a hard drive.  This makes a bootable OS in Linux and is portable from system unit to system unit.

---

### Post by James Wilde on 2016-02-24
Thank you Sudodus, Oldfred and Goofprog for your patience.

I have now run test -d <some parameters I have forgotten> && UEFI || Bios, which will tell me whether I am booting via EIF or bios, and I got the answer bios.

I assumed that the problem I was having was related to the fact that it is a usb stick which I'm trying to boot from, so I found an old disk with three partitions, a system partition and two Windows partitions, erased one of the Windows partitions and installed Ubuntu to that partition.  I tried booting from that partition and... nothing happened.  So now I assume it is not that it is a usb stick that gives me the problem.  It is the fact that I am trying to boot from usb.

I bit the bullet, managed to run unetbootin and make it see my usb stick (had to format it as MSDOS first) and installed Ubuntu that way, and guess what - it still won't boot.  I've checked the bios on this machine and booting from usb is allowed.  So now I don't know what more I can try.  Yes, I do.  I'll start up the computer into OSX with the alt key pressed so I get to choose my boot unit, and see what that does.  It works fine for different versions of OSX.  But first I'll post this so it doesn't get lost.

Later:  The Alt-start combination doesn't work on this machine, so nothing to try.  <sigh>

---

### Post by sudodus on 2016-02-24
Is there a boot flag on the boot partition (of Unetbootin)?

When the pendrive is inserted, please run the following command

```
sudo parted -ls
```

If still problems with the pendrive 'make by' Unetbootin (if/when there is a boot flag), you can try according to the following link. It makes pendrives that boot in the HP laptops in my family.

[A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

---

### Post by oldfred on 2016-02-24
While you mentioned OSX in first post, are you installing to a Mac?
Better to be in Apple sub-forum where those who know the differences can help.
Mac requires UEFI boot on gpt partitioned drives.

And I do not understand all the different models, as each seems a bit different.

---

