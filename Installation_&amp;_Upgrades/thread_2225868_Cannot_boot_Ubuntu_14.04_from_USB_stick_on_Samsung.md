---
title: "Cannot boot Ubuntu 14.04 from USB stick on Samsung Series 7"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by socheon on 2014-05-23
I  used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) to create a bootable USB flash drive for Ubuntu 14.04 64-bits.

It works on my other Lenovo laptop but strangely not my Samsung laptop. Anyone had any similar experience?

I have attached screenshots of the boot menu. My Samsung laptop did not find any USB device.

I have also attached screenshot of the Advanced Tab. All settings looked alright to me. Enabling or disabling UEFI support don't seem to resolve the problem.

---

### Post by oldfred on 2014-05-24
Your settings in UEFI show first choice is FDD or floppy drive and you have CSM/legacy on or BIOS boot not UEFI boot.
Generally better to have UEFI boot on. And most systems see a flash drive as another hard drive. My old system has many USB boot choices, none will boot a flash drive. But when I look at hard drives to boot my flash drive becomes one of the hard drive choices.
System will only show a correctly bootable flash drive that was plugged in when booting as a boot choice.
If Ubuntu 64 bit installer, it should show twice, once as UEFI and once as Legacy/BIOS/CSM.

In a Dell thread there was a comment that with many Intel systems you need to leave legacy boot on, but still boot in UEFI mode. Not sure if other systems can even do that.

---

### Post by socheon on 2014-05-26
Thanks oldfred. Seemed like it's going to take a lot of effort to find out the problem with USB.
I went to buy some dvds and it booted fine now.

---

