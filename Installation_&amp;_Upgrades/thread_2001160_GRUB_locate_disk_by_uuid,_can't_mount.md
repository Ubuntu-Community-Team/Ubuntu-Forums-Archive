---
title: "GRUB locate disk by uuid, can't mount"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by ath88 on 2012-06-10
Hello,

I have trouble booting my newly installed system.

To avoid another problem with graphics drivers (quite another history) it has been necessary for me to install Ubuntu 12.04 by different means than usual.

I connected the 120gb SSD disk through a SATA-to-USB cable (with external power to the disk, ofcourse) to my laptop. I then opened VirtualBox, mounted the physical SSD disk as a virtual disk[1] (this has previously worked perfect for me) and installed from the newly downloaded .iso of Ubuntu 12.04. I then installed the necessary graphics drivers that was necessary to boot on the intended hardware (the first problem).

I put the harddisk back in the chassis, and when booting i get through grub, but halt with a BusyBox promt. The error seems to be that grub attempts to mount the root partition by a uuid that doesn't exist in /dev/disk/by-uuid.

When i run 'mount /dev/sda1 /root' or 'mount /dev/sda /root' (which exists) i get an 'Invalid arguments'-error.

Now, how do i bootstrap the partition so i can update grub for proper automated booting of the system?

Thank you,
Asbjørn

[1] [http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software](http://www.sysprobs.com/access-physical-disk-virtualbox-desktop-virtualization-software)

---

### Post by wilee-nilee on 2012-06-10
Had you considered a install using the alternative cd?

---

### Post by drs305 on 2012-06-10
If your Ubuntu installation is on sda1, and set up normally, try this at the grub menu.

Press c to get to the grub prompt if not already there.

```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz ro root=/dev/sda1
initrd /initrd.img
boot
```

If that doesn't work, I'd recommend booting a LiveCD, installing Boot Repair, and allow it to attempt a fix. Link is in my signature line.

---

### Post by ath88 on 2012-06-13
> **wilee-nilee said:**
> Had you considered a install using the alternative cd?

I am not aware of any alterantive CD and have not seen it mentioned anywhere. Can you elaborate? :)

- ath88

---

### Post by drs305 on 2012-06-13
[http://www.ubuntu.com/download/desktop/alternative-downloads]("http://www.ubuntu.com/download/desktop/alternative-downloads")

---

