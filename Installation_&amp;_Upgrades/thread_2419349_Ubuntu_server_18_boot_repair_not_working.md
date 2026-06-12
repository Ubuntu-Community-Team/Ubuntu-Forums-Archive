---
title: "Ubuntu server 18 boot repair not working"
date: 2019-05-20
forum: Installation &amp; Upgrades
---

### Post by ubcsc on 2019-05-20
I'm not sure if I selected the right sub-forum. My apologies if I didn't.

Some days ago I had to hard reset(power cycle) my Ubuntu server which is running on an Intel NUC.

After that it didn't boot any more. Directly after bios info it goes to a blinking dash. I do not get the GRUB menu.

I tried boot repair by booting a live usb with ubuntu desktop, without any success.

It seems it doesn't recognize my disk anymore. Nevertheless when I use blkid or fdisk I can see my disk.  I'm using 1 nvme SSD.

Please see attached report by boot-repair.

I hope someone is able to analyze it and help me further. Please let me know if any extra details are needed.

[http://paste.ubuntu.com/p/ZwFtcHq3JH/](http://paste.ubuntu.com/p/ZwFtcHq3JH/)

---

### Post by ubcsc on 2019-05-20
SO when I unplug my USB drive which is needed to run live Ubuntu, it does recognize my SSD. But still no success.

[http://paste.ubuntu.com/p/tbrV5VsYHH/](http://paste.ubuntu.com/p/tbrV5VsYHH/)

---

### Post by oldfred on 2019-05-20
Do not know LVM.
But is nvme0n1p1 your ESP - efi system partition.
It looks like you had UEFI boot and would have to have an ESP as FAT32, but it also now looks like it will not mount.
If so try dosfsck on that partition from live installer.

sudo fsck.vfat -t -a /dev/nvme0n1p1
see also
man dosfsck

---

### Post by ubcsc on 2019-05-21
So above didn't work.
Also I do not use EFI.

After struggling for almost a week now I decided to reinstall my server. I wiped my disk, with its partitions. Reinstalled everything went okay, but after the first reboot I got: A bootable device has not been detected. 
In my visual bios setup I have disabled UEFI boot and enabled lecacy boot. (this was the same situation is before).

So still not working.

Now here is the strange part. When I boot with F10, into my boot device menu, select the harddisk-> it boots normally. 
Again, after reboot it comes back with the error A bootable device has not been detected.

What goes wrong here?

---

### Post by oldfred on 2019-05-21
It seems like your UEFI/BIOS is defaulting to UEFI boot. And only then when you manually select the BIOS boot, does it work.
Or is the hard disk entry really an UEFI fallback, which grub in UEFI mode also installs.

On my desktop, I have to have UEFI set to UEFI only, even UEFI or BIOS/CSM/Legacy mode only booted in BIOS mode when I was installing. Have not tried BIOS boot since old BIOS system died.

Have seen other posts with users with LVM and issues booting, usually from upgrades I think, but I do not follow LVM issues as I really do not know it.

---

