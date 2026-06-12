---
title: "Kubuntu &amp; Windows 10 dual-boot TPM"
date: 2018-09-08
forum: Installation &amp; Upgrades
---

### Post by Godspell on 2018-09-08
I've got my Windows 10 Pro on an SSD and got another free SSD which I'm thinking of putting Kubuntu on. Also got a TPM on my motherboard which is holding the key for W10 wholedisk encryption.

How can I install Kubuntu with wholedisk encryption using TPM (so I don't have to enter the password on startup) whilst maintaining the current W10 setup? Is it possible to have a dual-boot like this?

---

### Post by yancek on 2018-09-08
If you are new to Linux, probably the simplest thing to do is to create a bootable usb for Kubuntu with the proper software or burn the Kubuntu iso file to a DVD as an image and then boot whichever you use.  Also, taking out the windows SSD if that is possible would simplify things.  Another potential problem is UEFI which windows 10 almost certainly uses so you would need Kubuntu installed UEFI.  The link below discusses dual booting windows on a UEFI system.  Read at least the beginning and General Principles which should help.  Much of the rest of it is specific to Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2018-09-08
If you are new to Linux, probably the simplest thing to do is to create a bootable usb for Kubuntu with the proper software or burn the Kubuntu iso file to a DVD as an image and then boot whichever you use.  Also, taking out the windows SSD if that is possible would simplify things.  Another potential problem is UEFI which windows 10 almost certainly uses so you would need Kubuntu installed UEFI.  The link below discusses dual booting windows on a UEFI system.  Read at least the beginning and General Principles which should help.  Much of the rest of it is specific to Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I don't know what TPM is so can't help there.

---

### Post by Godspell on 2018-09-08
> **yancek said:**
> If you are new to Linux, probably the simplest thing to do is to create a bootable usb for Kubuntu with the proper software or burn the Kubuntu iso file to a DVD as an image and then boot whichever you use.  Also, taking out the windows SSD if that is possible would simplify things.  Another potential problem is UEFI which windows 10 almost certainly uses so you would need Kubuntu installed UEFI.  The link below discusses dual booting windows on a UEFI system.  Read at least the beginning and General Principles which should help.  Much of the rest of it is specific to Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I don't know what TPM is so can't help there.

I've already got a Kubuntu bootable USB and have previously installed and dual-booted it with W10; these aren't the problem. Neither is the UEFI.

Also, why would I take out the Windows SSD when installing Kubuntu?? That would make Kubuntu to not auto-detect W10 bootloader and prevent it from creating GRUB menu (where I can select different boot entries).

The issue here is TPM (Trusted Platform Module) that saves the key for wholedisk encryption in it, and I'm not entirely sure when (or how) the TPM needs to be invoked (during OS installation stage or afterwards). Or whether the Windows wholedisk encryption key that is currently saved in TPM would be overwritten by that of the Kubuntu.

When I previously dual-booted W10 with Kubuntu, the latter didn't detect the TPM at all. That's why.

Does anybody know how to work this?

Thank you.

---

### Post by yancek on 2018-09-08
> Also, why would I take out the Windows SSD when installing Kubuntu??  That would make Kubuntu to not auto-detect W10 bootloader and prevent it  from creating GRUB menu (where I can select different boot entries).


You gave no indication that you had ever installed any Linux so there was no way for use to know your level of knowledge.  The primary reason that is recommended for new users is so that they don't accidentally an already installed system.  It is a very simple process with a single, simple command to update grub and add a new system to the menu.

I don't know anything about TPM so you might try to see if they have a support site of their own.

---

