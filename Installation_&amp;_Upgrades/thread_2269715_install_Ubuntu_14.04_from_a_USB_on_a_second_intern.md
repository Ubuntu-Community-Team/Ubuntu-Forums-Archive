---
title: "install Ubuntu 14.04 from a USB on a second internal drive"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by Colin_Garcia on 2015-03-17
My main boot drive for Windows is a 250GB Samsung 840 Evo SSD and I created an NTFS partition on a different 2TB HDD to install Ubuntu on. I burned the Ubuntu iso onto a USB with Rufus and was wondering what options to select when I'm in the Ubuntu installer to successfully install the os on my partition on the 2tb HDD? Thanks.

---

### Post by Dennis N on 2015-03-17
> I created an NTFS partition on a different 2TB HDD to install Ubuntu on

NTFS will not work. Ubuntu would need an ext4 partition.

---

### Post by sudodus on 2015-03-18
Do you want to install Ubuntu into the whole USB HDD, or do you want to install Ubuntu into part of the HDD and have another (maybe bigger) part of it for sharing data with access from Windows and linux?

---

### Post by Colin_Garcia on 2015-03-20
> **Dennis N said:**
> NTFS will not work. Ubuntu would need an ext4 partition.
Thanks. Formatted it to ext4 using Minitool.

> **sudodus said:**
> Do you want to install Ubuntu into the whole USB HDD, or do you want to install Ubuntu into part of the HDD and have another (maybe bigger) part of it for sharing data with access from Windows and linux?

I don't have the intention of sharing the files as I'm just using Ubuntu for developing kernels for an Android phone. I installed Ubuntu onto an 120GB ext4 partition on my 2TB internal hard drive.

Now I have another issue- when I reboot my computer (even when in the boot menu I select to boot from my SSD to Windows) I always boot to Ubuntu. How do I prevent this from happening so that I can boot back into Windows as well?

---

### Post by sudodus on 2015-03-20
If Windows is installed in UEFI mode and Ubuntu is installed in BIOS/CSM mode, you need to switch mode (in the UEFI/BIOS) menu system for the other operating system to boot.

If both operating systems are installed in BIOS/CSM mode, it should be enough to run

```
sudo update-grub
```

in Ubuntu to get an entry in the grub menu for Windows (and you can select operating system easily).

If both operating systems are installed in BIOS/CSM mode, it might work with

```
sudo update-grub
```

but you might also need to run Boot Repair to make it work. See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See this link and links from it for more information about UEFI

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by Colin_Garcia on 2015-03-20
> **sudodus said:**
> If Windows is installed in UEFI mode and Ubuntu is installed in BIOS/CSM mode, you need to switch mode (in the UEFI/BIOS) menu system for the other operating system to boot.

If both operating systems are installed in BIOS/CSM mode, it should be enough to run

```
sudo update-grub
```

in Ubuntu to get an entry in the grub menu for Windows (and you can select operating system easily).

If both operating systems are installed in BIOS/CSM mode, it might work with

```
sudo update-grub
```

but you might also need to run Boot Repair to make it work. See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See this link and links from it for more information about UEFI

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

I installed Ubuntu in UEFI mode but I'm not sure what I installed Windows on. It was just a DVD that I booted from to install. Is there something for this case?

---

### Post by sudodus on 2015-03-20
I think Windows boot into the mode that is set in the UEFI/BIOS menus. If you do not remember that you changed the boot mode, and Ubuntu is installed in UEFI mode, I think Windows is also installed in UEFI mode, but you should check it. ***Boot-Repair*** might be able to fix the problem in UEFI mode.

---

