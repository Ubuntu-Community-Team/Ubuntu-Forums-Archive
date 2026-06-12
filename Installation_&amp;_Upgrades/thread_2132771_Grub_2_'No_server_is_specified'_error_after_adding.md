---
title: "Grub 2: 'No server is specified' error after adding entry in 40_custom"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by actetylcholine on 2013-04-05
Hi,

I'm trying to add a new entry to the Grub 2 boot menu. The goal is to have the option to boot into a live linux OS called [Bankix]("http://www.heise.de/ct/projekte/Sicheres-Online-Banking-mit-Bankix-284099.html") (derived from Ubuntu 12.04 and geared towards safe online banking). Bankix is installed on a SD memory card on /dev/sdc1. From what I understand, I need to edit /etc/grub.d/40_custom to make a new entry appear in the Grub 2 boot menu. I added the following:


menuentry 'Bankix' {
insmod chain
set root=(hd2)
chainloader +1
}


When I select this option from the Grub 2 menu on startup, I get an error: 'no server is specified'. Googling this error message does not return any useful results unfortunately, so I'm unsure how to tackle this issue. I'm using Ubuntu 12.10 with Windows 8 dual boot. Can anybody help? See also [this]("http://ubuntuforums.org/showthread.php?t=2132748") thread where Darkod helped me out with my first issue in relation to this project.

Thanks!

---

### Post by ahallubuntu on 2013-04-05
~

---

### Post by actetylcholine on 2013-04-06
Hi ahallubuntu,

thanks for the reply. I tried that, and this is the output:

Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found Windows 8 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda6
Adding boot menu entry for EFI firmware configuration
done

There is no mention of /dev/sdc or /dev/sdc1 - does this mean that Ubuntu didn't pick up on the OS on the SD card? If so, how can I get Ubuntu to discover the OS on the card?

Thanks!

---

### Post by darkod on 2013-04-06
If you are talking about live OS (live environment), update-grub can't find it and add it in grub. It finds only installed OSs.

What is it that you actually want to do? Run a live OS for doing your online banking so that you have better protection? In that case simply boot the computer from the SD card when ever you need to, and that's it. No need to add it to grub2 since you will not be using it all the time.

Otherwise the option would be to make an entry in grub2 to boot the ISO (or live environment) from the card. The chainloader can't work because you actually don't have a bootloader on the card, you have no OS installed, right?

The chainloader option can't boot ISO or live environment, it only chainloads to installed bootloaders. It all depends how you created the card. Did you just copy the ISO on it? Did you just unpakced the ISO on it?

You need to prepare it as bootable device, not simply copy the ISO to it. Only in that case grub2 can chainload to it.

---

### Post by actetylcholine on 2013-04-06
Hi Darko, 

thanks for your reply. Yes, the goal is to boot the live OS from the SD card in order to have better security around online banking. Unfortunately the BIOS in my laptop does not allow for booting from an SD card, that's why I need to work around this by adding the option to the Grub 2 boot menu. 

There should be a bootloader on the SD card. I used [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable SD card from the ISO file. I tested the SD card on a friend's laptop and the machine booted with the SD card no problem.

Your help is much appreciated!

Thanks!

---

### Post by darkod on 2013-04-06
In that case the set root=(hd2) should be enough provided your laptop is not stopping grub2 boot it. Did you check if hd2 is mapped to /dev/sdc in the device map?

As I said before, create a new grub2 device map with:
sudo grub-mkdevicemap

That will also show the mapped devices. There should be an entry mapping hd2 to /dev/sdc. If there isn't, you can't use the chainloader command and need to think of grub2 booting the live mode directly instead.

---

### Post by actetylcholine on 2013-04-06
Hi Darko,

this is what /boot/grub/device.map looks like on my laptop:

(hd0)	/dev/disk/by-id/ata-Hitachi_HTS545050A7E380_TE85113RJY8KNR
(hd1)	/dev/disk/by-id/ata-SanDisk_SSD_i100_24GB_124000102598
(hd2)	/dev/disk/by-id/usb-Generic_STORAGE_DEVICE_000000000207-0:0

hd0 is the main SATA drive, hd1 is the fast boot SSD drive and hd2 should be the SD card, since there is no other drive attached. I already ran sudo grub-mkdevicemap. I hope this means that the mapping is ok? 

Thanks!

---

### Post by darkod on 2013-04-06
Yeah, it looks like the mapping is OK and hd2 is correct.

It doesn't work as it is?

---

