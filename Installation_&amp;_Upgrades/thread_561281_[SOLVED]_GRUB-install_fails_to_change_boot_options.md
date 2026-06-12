---
title: "[SOLVED] GRUB-install fails to change boot options in MBR"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by adelaar on 2007-09-27
Hi,

I just installed kubuntu 7.04 on an HP pavilion tx1250eg. First, the live CD didn't even boot on the notebook (hanging after "loading hardware drivers"), but turning on the option 'noapic' helped, and kubuntu installed successfully. After installing grub on the MBR, however, the system still hangs during boot time, although grub boots my shrinked windows partition on /dev/sda1. So I tried to turn on 'noapic' also for the MBR.

First, I tried to edit the boot options in grub's start up menu (typing "e"), but it immediately forgets my edited options, whatever I do.
Then I booted my system with a live CD, and tried to fix the MBR:
I used the following commands (sda2 is my root partition, no separate partition for /boot!):
```

sudo mount /dev/sda2 /media/sda2
```
I edited menu.lst in /boot/grub, inserting a line that says 'noapic', then did
```

sudo grub-install --root-directory=/media/sda2 /dev/sda
```
with kubuntu AND knoppix live CDs. Didn't seem to change anything.

With the kubuntu live CD, I tried a last approach:
```

sudo mount /dev/sda2 /media/sda2
sudo mount -o bind /dev /media/sda2/dev
sudo mount -t proc /proc /media/sda2/proc
sudo chroot /media/sda2
grub-install /dev/sda2

```
The last command results in the message:
```

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
```
But whatever I do, at boot time there are no changes in grub's options.

According to MS Windows' device manager, my sata hard drive /dev/sda is a 'WDC WD16 00BEVS-60RST SCSI disk drive'. It's the only hard drive of the system.

So what can I do here? Does anybody have an idea how to boot with 'noapic' turned on permanently? Thanks for all help!

---

