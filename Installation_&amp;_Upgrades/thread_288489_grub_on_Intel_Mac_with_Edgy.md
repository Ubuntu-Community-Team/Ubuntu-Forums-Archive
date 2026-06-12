---
title: "grub on Intel Mac with Edgy"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by earth2mark on 2006-10-29
I was hoping Edgy would allow grub to work on an Intel Mac, but unfortunately I get the following:


$ sudo grub-install /dev/sda3

The file /boot/grub/stage1 not read correctly.


Can anyone shed light on whether its possible to make grub work with Edgy on an Intel Mac?

---

### Post by matcram on 2006-10-30
mine worked without doing anything. Sorry for you... Maybe try to reinstall.

The problem i am currently facing, is that sometimes when i want to reboot, it doesn't reboot. It gets stucked after the "short mac song", grub doesn't launch and my monitor goes in sleeping mode... Pretty weird. I have to manually power off the mini and then start it normally.

---

### Post by earth2mark on 2006-11-01
> **matcram said:**
> mine worked without doing anything. Sorry for you... Maybe try to reinstall.

The problem i am currently facing, is that sometimes when i want to reboot, it doesn't reboot. It gets stucked after the "short mac song", grub doesn't launch and my monitor goes in sleeping mode... Pretty weird. I have to manually power off the mini and then start it normally.

What version of grub are you using?  Can you post the exact line from aptitude or something similar?

What Mini are you using exactly?

So you are saying you just did apt-get install grub and rebooted and it worked?  You didn't have to run grub-install?

Can you tell me specifically what you did?

Thanks.

---

### Post by gpremuda on 2006-11-27
> **earth2mark said:**
> I was hoping Edgy would allow grub to work on an Intel Mac, but unfortunately I get the following:


$ sudo grub-install /dev/sda3

The file /boot/grub/stage1 not read correctly.


GRUB gives this error message when the partition type doesn't match the file system on the partition. The problem is than rEFIt gptsync sets the partition type ion the MBR partition table to FAT32/EFI even if the GPT partition entry is set to ext3. I've tried setting the partition type with fdisk (which only edits the MBR partition) and avoid resync, and grub-install works, but I still cannot boot with grub (and reinstalling lilo doesn't work anymore)

---

