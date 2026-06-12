---
title: "Stuck in grub2. Please help!"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2016-07-28
Hello, everybody,

I have been moving and resizing partitions with gparted, but I forgot to run update-grub after that. Now, the system boots to a grub2 command line (version 2.02-beta2-9ubuntu1.3, if you need to know).

I would like to boot again from the USB to run update-grub and hopefully fix the boot menu, but I am not familiar with grub.

ls shows a list of partitions, and (hd0,msdos1) looks like the bootable USB. There are also a few partitions in (hd1, ...) but I don't think any of them is usable.

I have tried the following, which I read [here]("http://blog.viktorpetersson.com/post/93191892924/how-to-boot-from-usb-with-grub2"):

```
linux (hd0,msdos1)/ntpasswd/vmlinuz root=/dev/sdb1
initrd (hd0,msdos1)/ntpasswd/initrd.cgz
boot
```

But it hangs. Any ideas?

---

### Post by skamarla on 2016-07-28
Bump!

I have been looking at the partitions in the hard disk, and one of them shows promise:

```
ls (hd0,gpt2)/efi/ubuntu
./ ../ grubx64.efi shimx64.efi MokManager.efi grub.cfg

```

But I don't know what to do with them.

Could it be that EFI is the problem, and I have to use the commands "linuxefi"? But then I get the error "kernel doesn't support EFI handover". Maybe another bootable distribution?

Right now, it's all but bricked...

---

### Post by sudodus on 2016-07-28
If you move the head end of the partition, that grub points to, it will not find it. The solution is to reinstall grub with grub-install. See this link

[Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

It is also possible to fix it with the Boot-Repair disk (rather automatically).

[Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2016-07-28
Grub does not use the same partition labels as Linux.

hd0 = first hard disk. hd1 = second hard disk and so on. msdos1 = first partition. msdos2 = second partition and so on.

You do not explain your partition layout. Do you have one hard disk or two? If you only have one hard disk then root=/dev/sdb1 would be wrong as it points to the first partition on the second hard disk (sdb). Then you report this hdo, gpt2. That is the second partition on the first hard disk.

gpt would indicate a GPT partitioning scheme. Whereas, msdos would be for an MBR partitioning scheme. So, which is more accurate hd0,msdos1 or hd0,gpt2? I am too confused to give accurate advice.

Regards.

---

### Post by skamarla on 2016-07-28
I only have one hard disk. When I started with a USB disk plugged in, this was labeled as hd0, and the system disk was hd1. If I didn't plug the USB disk, I only had hd0. Hence the mismatch. (hd0,msdos1) was the only partition of the USB disk; (hd0,gpt2) was a partition of the system disk when I had booted without the USB drive.

I am more or less on my way now: problem is that the BIOS wouldn't boot from the USB disk, and the main disk's grub is all messed up and needs an update-grub. I have now managed to bring up the BIOS (it's a Lenovo Z500, so you need Fn+F2) and booted on Windows. So it's not bricked, only handicapped. Later, I'll try to get the BIOS to recognize a repair drive and refresh grub's configuration.

Thanks a lot for your interest.

---

### Post by grahammechanical on 2016-07-28
It would not do any good reinstalling Grub onto the USB stick, now, would it.

Run the live session. Use File Manager to open the hard drive. That will mount the drive. then in a terminal it should be

```
sudo grub-install /dev/sda
sudo update-grub
```

In a live session it may even work with the prefix of sudo.

Regards.

---

