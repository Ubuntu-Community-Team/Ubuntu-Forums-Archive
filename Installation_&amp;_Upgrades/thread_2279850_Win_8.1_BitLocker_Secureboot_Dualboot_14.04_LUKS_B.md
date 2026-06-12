---
title: "Win 8.1 BitLocker Secureboot Dualboot 14.04 LUKS /Boot on USB"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by paranoidandroid2 on 2015-05-26
Hi Ubuntu community,

till now I have found a all the help I needed through search engines and browsing through ubuntu forums.
Unfortunately my latest build is a little more complicated/exotic and I can’t figure out on my own how to implement it. So I’ve registered here to ask for your help and I’m sure that this will come in handy for others as well.

So here goes:
my new Notebook (Asus UX303LN) came with windows 8.1.
I have been able to encrypt Windows using bitlocker and install ubuntu encrypted with LUKS along side in UEFI mode and Secureboot enabled using this tutorial [http://wiki.ubuntuusers.de/System_verschl%C3%BCsseln](http://wiki.ubuntuusers.de/System_verschl%C3%BCsseln). The partition scheme looks something like this

/dev/sda1 (windows re)
/dev/sda2 (efi)
/dev/sda3 (windows reserved)
/dev/sda4 (windows)
/dev/sda5 (/Boot)
/dev/sda6 (LUKS)

As far as I understand /Boot is a vulnerability as ists not encrypted and malware caught through windows could manipulate it and jeopardize the security of my ubuntu system.
To circumvent this problem I want to install the /Boot partition on a usb drive.
So far I have been unsuccessful using either of these setups.

A (preferred)
/dev/sda1 (windows re)
/dev/sda2 (efi)
/dev/sda3 (windows reserved)
/dev/sda4 (windows)
/dev/sda5 (LUKS)
/dev/sdb1 (/Boot)

As I understand Grub2 located in /dev/sda2 is having problems finding /Boot on the USB drive (/dev/sdb1)


B (if necessary)
/dev/sda1 (windows re)
/dev/sda2 (efi)
/dev/sda3 (windows reserved)
/dev/sda4 (windows)
/dev/sda5 (LUKS)
/dev/sdb1 (efi)
/dev/sdb2 (/Boot)

I think the firmware of the notebook won’t accept /dev/sdb/ as efi because its not signed.
What am I doing wrong? Thank you for your kind help :)

The ParanoidAndroid

---

### Post by oldfred on 2015-05-26
No idea what bitlocker has done to system.
And with Secure boot you may have to separately turn on or allow boot from USB, which may not be possible with some systems and secure boot on.

If you look in /EFI/ubuntu there will be a small grub.cfg.
It is just a configfile entry to the grub.cfg in /boot. You should be able to just edit that to have correct UUID/partition for /boot.

       In efi partition's folder /EFI/ubuntu add another grub config to tell UEFI where to find grub.cfg with just this one line
configfile (hd0,gpt7)/boot/grub/grub.cfg

This is the file you will see but the version above it really the same without the search.

   search.fs_uuid Your-uuid-here root hd0,gpt8
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

With secure boot on, kernels & grub are signed, so absolute worst case would be corruption of /boot partition. But Windows systems do not see or mount ext formatted partitions normally, so you should not have much chance of issues.
The only major boot virus with BIOS was actually Sony with its DRM.

---

### Post by paranoidandroid2 on 2015-06-02
Thank you oldfred!

mounting dev/sda2 as /boot/efi during installation did the trick.
It boots just fine.
/boot/efi/EFI/ubuntu/grub.cfg looks like this

search.fs_uuid <my UUID> root hd2,gpt1
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

But if
sda2 is /boot/efi
and
sdb1 is /boot

shouldn't it be hd1,gpt1?

---

### Post by oldfred on 2015-06-02
I had many drives in my old BIOS system. And they always were in SATA port order. But I must have skipped a port as when I plugged in a flash drive it was sde. But on reboot it became sdb and every other drive changed a letter. I had to be careful on device order.

With my new UEFI system somewhat similar and I suspect I plugged DVD in second port. My installs to sdb often say hd2, but drive is sdb. I have had to manually change some entries in flash drives to get them to work.

Or I really do not know, best to experiment.

---

