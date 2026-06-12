---
title: "Failed Boot Repair"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by Marc_Schoenauer on 2015-09-11
Hi [apologies if this is not the right forum, and thanks to redirect me in that case]



After accidentally removing the vmlinuz file in /boot, I followed the instructions given on [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) to re-install the kernel (boot on a USB stick, chroot to the damaged disk, re-install linux-image-generic and reboot.

I tried then tried BootRepair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and pressed the "recommended repair" button, but though the final message was that the system had been repaired, it didn't re-boot either.

The error message from GRUB is always the same:



ALERT! /dev/mapper/ubuntu--vg-root does not exist. 


I'm using version 14.04, kernel 3.13.0-61 (also tried to install -62) - makes no difference.


The BootInfo URL is  [http://paste.ubuntu.com/12354496](http://paste.ubuntu.com/12354496)



Any help would be much appreciated.

Thanks

Marc

---

### Post by jean_rivire on 2015-09-12
Hum, not being a crack but saving your files can't hurt if there is a boot problem, try make a usb-boot, escape installation in order to be directed to a kind of 'desktop', there you will be able to see your files, to put them on the cloud...

Once that is done, just restart and do the full install, since you have to reinstall the kernel anyway, I guess once the files are saved you could do full install, erase the disk and start fresh

But I mean if you want somebody more pro on this, wait for another answer!

Cheers

---

### Post by Bucky Ball on 2015-09-12
Welcome. sda5 is an encrypted partition. That looks like the problem.

I don't know anything about them, but I will ask how you installed this in the first place and what release you are using. sda1 is an old EXT2 filesystem partition and EXT4 is now commonly used. There is also no /swap partition, unless that's the encrypted sda5.

* Here you go, from your bootinfo:

```
mount: unknown filesystem type 'crypto_LUKS'
mount **/dev/sda5** : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32
Disk /dev/mapper/luks-cf479057-5300-4008-b8c9-6e7c1398ce6e doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by Marc_Schoenauer on 2015-09-12
Thanks, guys.
The install was made with data encryption - this might be the cause of the problem indeed.
I tried to install grub, using instructions at [http://ubuntuforums.org/showthread.php?t=2266650](http://ubuntuforums.org/showthread.php?t=2266650) but it didn't help.
I guess I'll have to follow Jea-riviere's advice and reinstall from scratch - without data encryption this time.
Cheers
Marc

---

### Post by Bucky Ball on 2015-09-13
You didn't read my post? It IS the problem.

If you intend to reinstall, please mark this thread as solved and post a new one for any further problems. Thanks.

---

