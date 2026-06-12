---
title: "Two startup OSs on one USB stick?"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Ederico on 2010-12-10
Dear all,

Is it possible to use one USB stick having two startup OSs? I would like to get an 8GB USB stick and use it to have a startup stick. I would to have both Ubuntu and Kubuntu.

Is that possible?

Regards,
Ederico.

---

### Post by wojox on 2010-12-10
Something like [This?]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")

---

### Post by Ederico on 2010-12-10
That should be it, thanks!

I'll try it out as soon as I buy a new USB stick.

---

### Post by C.S.Cameron on 2010-12-10
another option I like is MultiBootUSB:

[http://sourceforge.net/projects/multibootusb/](http://sourceforge.net/projects/multibootusb/)

---

### Post by marcostg85 on 2010-12-10
But is it possible have something like this in the usb?

Partition 1. Ubuntu Netbook
Partition 2. Windows 7 Installer
Partition 3. Generic Document Space

---

### Post by C.S.Cameron on 2010-12-11
I have not tried it but I would think that if you used the grub2 method per MultiBootUSB you could make your first partition FAT32 for document space, (Windows only sees the first partition on a flash drive).
Second partition should be formatted NTFS with the Win7 disk copied to it, (or iso extracted to it). 
The Netbook iso would be on the third partition.
Grub2 would be installed to the disk with menuentries pointing to Win7 and Netbook.

---

### Post by marcostg85 on 2010-12-11
but is it possible to have Ubuntu Netbook to but as a normal OS from the usb and having the Windows 7 Installer too?

---

### Post by C.S.Cameron on 2010-12-11
> **marcostg85 said:**
> but is it possible to have Ubuntu Netbook to but as a normal OS from the usb and having the Windows 7 Installer too?

On second thought the Netbook iso would go on the first partition, the FAT32 one.
Grub2 will boot an Ubuntu iso.

If you want a Full install of Netbook, then it would go on the third partition, which would be ext3 or ext4.

I have not tried a grub2 menuentry for booting Windows 7 install but think it should be possible.

---

