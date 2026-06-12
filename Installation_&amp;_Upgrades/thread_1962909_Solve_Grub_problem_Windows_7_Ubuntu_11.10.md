---
title: "Solve Grub problem Windows 7 Ubuntu 11.10"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by kabeza on 2012-04-21
Hi
I've got a samsung laptop with Windows 7. I ran Ubuntu 11.10 install from CD and all went ok. I want to have dualboot.

Then I restarted PC without Ubuntu CD and noticed Windows started. I didn't see Grub menu. So I ran liveCD again, and tried:

```
sudo fdisk -l
```

[http://paste.ubuntu.com/940325/](http://paste.ubuntu.com/940325/)

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /mnt/sda
sudo umount /mnt
sudo reboot
```

The above procedure went ok, without errors and restarted. I went pissed when got a "File not found" error message then grub recovery. So I started liveCD again and got a Boot Info Script log

[http://paste.ubuntu.com/940317/](http://paste.ubuntu.com/940317/)

Can anyone tell me which is going wrong? And how could I solve this?
Did I install grub correctly in sda1? or should I have done into sda2?

Thanks,

---

### Post by darkod on 2012-04-21
You needed to mount the root partition, and you mounted sda1 which is the win7 boot partition.

Boot into live mode with the cd and move /boot/grub/core.img from /dev/sda1 to /dev/sda6.

Then open terminal and try:
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart without the cd and see if that helped.

---

### Post by kabeza on 2012-04-21
Hi
Thanks for helping but can't find core.img in /dev/sda1 (/boot/grub/)
Only found core.efi file

---

### Post by darkod on 2012-04-21
Hmm, weird. You would have core.efi file if you use EFI boot. But in that case the first partition on the disk needs to be the EFI system partition, and in your case it is not.

Besides, the script reports core.img file on sda1.

Take a look in your BIOS and make sure you are using BIOS boot and not EFI boot.

---

### Post by kabeza on 2012-04-21
will check that option in BIOS and will launch liveCD again
Anyway, besides checking that option in BIOS, should I reinstall grub to /sda6 ?

I mean, how should I do to remove actual grub, and reinstall again to sda6? would that solve the problem too?

---

### Post by darkod on 2012-04-21
The grub2 bootloader needs to be installed onto the MBR of the disk, in other words /dev/sda.

If it has a number like /dev/sda6 that means partition #6. So, do not install it on a partition, in most cases it doesn't help.

The boot process starts from the MBR of the disk, so the bootloader goes there.

In some cases, you have one bootloader on the MBR and another on a partition, chainloaded to the main one. But with grub2 installing on a partition is not recommended, besides you don't need it.

---

### Post by kabeza on 2012-04-21
Hi again

Entered BIOS and there's an option 
**"UEFI Boot Support" which is enabled**

Then this is what I did from liveCD:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This made Windows to boot correctly again and avoid the:
"file not found" => grub recovery

**Now, Could I try**

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

to fix everything?

---

### Post by darkod on 2012-04-21
You can try, but maybe it will not work. During the install it detected the EFI mode and installed core.efi instead of core.img.

Try it anyway, and if it doesn't work you may need to reinstall grub2 from inside the installation with chroot.

---

### Post by kabeza on 2012-04-24
> **darkod said:**
> You can try, but maybe it will not work. During the install it detected the EFI mode and installed core.efi instead of core.img.

Try it anyway, and if it doesn't work you may need to reinstall grub2 from inside the installation with chroot.


OK. I'll try this weekend (parents house) and will reply back, but:

1) In case grub install into /dev/sda6 doesn't work, may I follow this tutorial (maybe with some mods regarding my partition setup)?
[http://zeldor.biz/2010/12/install-grub-from-chroot/](http://zeldor.biz/2010/12/install-grub-from-chroot/)

2) Do you advise me to disable that UEFI option in BIOS?

Thanks again for all the help

---

### Post by darkod on 2012-04-24
That is not a grub install into /dev/sda6. First you are mounting the root partition, /dev/sda6, because grub needs to know where it is. Then you use the grub-install to install grub2 on the target which is /dev/sda, the MBR of the disk. It should not have a number in it in the second command.

Yes, you can try a chroot procedure. That would be the backup plan. If simply adding grub2 to the MBR doesn't work, with chroot you can completely remove the grub2, and install again.

I don't use EFI but my board doesn't even have the option. Personally I see no benefit from it at this moment. Unless you have a specific reason for using it, and if your board allows it, I would say disable it. It's up to you. Ubuntu can work with EFI but in that case the install procedure is slightly different, and in any case you don't seem to be using EFI according to the partitions on the disk. Having the option enabled in BIOS is probably only confusing things.

---

### Post by kabeza on 2012-04-28
Finally tried and solved with this

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

thanks darkod

---

