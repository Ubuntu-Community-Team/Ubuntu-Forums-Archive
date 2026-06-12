---
title: "A bigger hard drive isn't supported?"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by RedPenguin on 2012-04-16
I have a Compaq Presario F739WM laptop (1.8GHZ/2GB RAM).

I have had Ubuntu installed on it for probably 3.5-4 years or so.

It came with a Hitachi 160GB drive and I had no installation issues.

Then that drive started to die and via warranty a 2.5 SATA Toshiba 160GB drive was put in.

Now the Toshiba 160GB which turned out to be total junk died fairly quickly.

Now I put in a WD 1TB drive in and Windows 7 installed with zero problems.

Yet the minute I tried Ubuntu I started getting issues.

11.10 and 11.04 (i386) Alternate Install randomly die during "Installing Software" saying an installing software failure.

For some reason also, Ubuntu 11.10 and 11.04 Desktop CDs (i386) appear to not even see the hard drive at all. Even using an 11.04 Live USB stick with persistence I had even refuses to see the hard drive only the USB stick using gparted and other methods.

How can just increasing the hard drive size cause such chaos?

---

### Post by darkod on 2012-04-16
It also depends whether win7 did something like GPT partition table during installation.

The live mode should see the disk correctly though. It is not listed at all as a device?

Check what BIOS says, although if BIOS doesn't recognize it it wouldn't exist for windows too.

---

### Post by haqking on 2012-04-16
did windows 7 use GPT or make the disk a dynamic disk ? instead of a basic disk ?

---

### Post by RedPenguin on 2012-04-16
Well according to Windows 7's Disk Management it's claiming it's a Basic Disk using MBR not GPT.

---

### Post by darkod on 2012-04-16
And how about ubuntu live mode (not the installer process)? Can it see it? If you try something like:
sudo fdisk -l

or
sudo parted /dev/sda unit s print

Another option, which is very rare on 2.5" disks, if it was used in raid it could have meta data remains. Windows ignores them but ubuntu installers not.

To remove, it would be:
sudo dmraid -E -r /dev/sda (of course, to run this live mode will have to see the disk as /dev/sda at all)

---

### Post by RedPenguin on 2012-04-16
> **darkod said:**
> And how about ubuntu live mode (not the installer process)? Can it see it? If you try something like:
sudo fdisk -l

or
sudo parted /dev/sda unit s print

Another option, which is very rare on 2.5" disks, if it was used in raid it could have meta data remains. Windows ignores them but ubuntu installers not.

To remove, it would be:
sudo dmraid -E -r /dev/sda (of course, to run this live mode will have to see the disk as /dev/sda at all)

Nope just tried both the fdisk and the parted commands, for some reason neither command find any hard drive at all.

EDIT: I did just notice some odd things in dmesg though.

[http://pastebin.com/AG3w51NA](http://pastebin.com/AG3w51NA)

This line being the most bizzare:

[    5.708216] ata3.00: model number mismatch 'WDC WD10JPVT-00A1YT0' != 'C WD10JPVT-00A1YT0                    &#65533;'

It appears to be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501950)

which I also have an NVidia MCP51.

---

### Post by RedPenguin on 2012-04-20
I finally got Ubuntu to install but then it destroyed itself.

Oh well, maybe one day I can find a solution but any Google Search/Forum Search just finds me people with the same problem with no solution.

---

### Post by RedPenguin on 2012-04-23
Oddly enough it appears that simply not having the hard drive pushed in tight enough may have just been the problem the entire time.

So far Ubuntu is working fine and except for my touchpad mouse not working at first (which used to happen at total random before the new HD) it has not been having any issues.

---

### Post by ledzepjes on 2012-04-23
be careful when using gparted, I've found it doesn't play nice with NTFS partitions created during windows installs, I would first use the disk shrink option in disk managemet in windows 7 to shrink the size of the partition. In windows 7 rt click "computer", click "management" then go to "disk management" and shrink the partition. Then reboot to the Ubuntu cd or Ubuntu usb and then install in the free space, I'd recommend making the freespace extended space, then install in that extended partition

---

### Post by ledzepjes on 2012-04-23
you have a 2.5 inch 1tb drive, is it 12mm or 9.5mm? high? it fits in your laptop drive bay? is that why it's not in all the way?

---

