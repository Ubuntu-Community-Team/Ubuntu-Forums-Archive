---
title: "Can my computer boot from external HDD?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Puzzled Guy on 2009-11-15
I own an MSi Wind U100 computer running the dreaded Windows. I am planning to install Ubuntu Netbook Remix onto an external hard drive. Can anyone tell me if my BIOS will support booting from from external HDD?

And while I'm at it, I DON'T WANT A DUAL-BOOT SYSTEM. I want to have it like this:
1. If I boot *with external drive plugged in *and it boots into Ubuntu.
2. If I boot *with external drive unplugged *and it boots into Windows.


Thanks to anyone who can help with one or both of these!

---

### Post by ed-koala on 2009-11-15
I don't believe you can set BIOS to boot to an external drive.  That means, the boot record will always be on your internal HD, which is what your BIOS will point to for booting.  Therefore, the bootloader program, like grub, is going to control your process.

This makes the question, can Grub, or other bootloader like Lilo, etc, check for an external drive and boot to it automatically? I doubt it, tho I don't know for sure.  If not, you are stuck with duel boot system and selecting what you want.

---

### Post by oldfred on 2009-11-15
It depends totally on your hardware. Most newer systems will during the BIOS boot show a key to press to choose where to boot, i.e. HD CD USB, if so it is possible. Even if it is a USB HD it will probably be a choice under the HD not USB.

Also in BIOS can you choose boot locations?

---

### Post by tsucol11 on 2009-11-16
I agree with Oldfred.. For my ASUS MB I press F8 and get the option to boot from whatever drive is connected to the MB including my ext USB HD. I believe you can also set up your bios to boot from USB as primary & your HD as secondary. Depends on the age of your MB.

Brian


> **oldfred said:**
> It depends totally on your hardware. Most newer systems will during the BIOS boot show a key to press to choose where to boot, i.e. HD CD USB, if so it is possible. Even if it is a USB HD it will probably be a choice under the HD not USB.

Also in BIOS can you choose boot locations?

---

### Post by moore.bryan on 2009-11-16
AFAIK, if you install everything (base system, grub, etc.) onto an external hard drive connected by USB and have your BIOS allowing a USB boot, then your BIOS should treat the external as if it was a flash drive.

---

