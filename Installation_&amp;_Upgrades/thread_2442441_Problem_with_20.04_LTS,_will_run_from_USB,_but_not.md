---
title: "Problem with 20.04 LTS, will run from USB, but not from installed on SSD"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by jake5012 on 2020-05-03
Hello,

I am trying to install 20.04 LTS Desktop on a Acer Aspire R3-131T laptop. Celeron N3160. 4GB RAM.  120GB SSD.  PC is working and was using Windows 10.

I downloaded the 20.04 ISO and followed the directions to install it on a USB drive.

The PC will boot from the USB drive and allowed the OS to run off the USB drive and allowed the installer to run.

Once the installation is complete, and it prompts to reboot and remove the install media, the PC does not detect a bootable OS.

Tried using UEFI mode and I get a "System BootOrder not found" message and it just keeps restarting and not making it past the BIOS

Using Legacy mode, and I get a "No Bootable Media Found"

I am fairly new to using ubuntu, so any help with this is appreciated.

---

### Post by CelticWarrior on 2020-05-03
Welcome.

Is the Windows preinstalled? If so it's in UEFI mode therefore NEVER change it to Legacy!
Assuming you installed Ubuntu correctly in UEFI mode then the only thing left to do is change the boot order to "Ubuntu" in UEFI settings.

If it doesn't work then better to see details instead of making another educated guess. Please use the 2nd option in a live session - installation of Boot Repair using a PPA -, do not use the old ISO. **Do NOT make any repair.** Click "Create a bootinfo summary" and post it here.

---

### Post by jake5012 on 2020-05-03
[https://paste.ubuntu.com/p/GjvmBnWmv2/](https://paste.ubuntu.com/p/GjvmBnWmv2/)

I also noticed that the BOIS does not have a Ubuntu in the UEFI settings, it has a linpus lite now.

---

### Post by CelticWarrior on 2020-05-03
So, because you posted the report without further comments, should we assume that what I first suggested didn't work? Or that you didn't try?

If you did try what were the boot options available?

---

### Post by jake5012 on 2020-05-03
Edited previous post.

I left it in UEFI.  Checked for Ubuntu and it wasn't there, but there was Linpus Lite.

Set that as the first boot options, but still have the same results

---

### Post by CelticWarrior on 2020-05-03
> **jake5012 said:**
> Edited previous post.

I left it in UEFI.  Checked for Ubuntu and it wasn't there, but there was Linpus Lite.

Set that as the first boot options, but still have the same results

A system that isn't there cannot boot, obviously. But it was there at some point and its bootloader is still present in the ESP (EFI System Partition). That issue isn't as relevant as you might think at first glance and can be dealt later (there's really no need - bootloaders by themselves do nothing in the absence of a system partition - but surely a cleanup can be done).

The report shows an ESP and a Linux partition using the rest of the drive so supposedly Ubuntu was correctly installed. For now you can try Boot Repair's recommended repair that with some luck will properly install the Ubuntu bootloader. 

Keep us posted.

---

