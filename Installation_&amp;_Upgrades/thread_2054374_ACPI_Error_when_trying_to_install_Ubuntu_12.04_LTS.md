---
title: "ACPI Error when trying to install Ubuntu 12.04 LTS from USB-stick"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by fritzhy on 2012-09-07
Hi!

It feels like I've Googled this for several hours now without getting any smarter. 

I just built myself a new computer, and of course I want to run Ubuntu on it. 

Components:

Motherboard: ASUS P8Z77-V Pro
CPU: Intel Core i5 3570K 3.4 GHz
GPU: MSI GTX 560Ti OC
RAM: 4x4GB Corsair Dominator 1600MHz

What happens when I try to install Ubuntu 12.04 LTS 64bit from my bootable USB-stick is that the install starts to load up normally, then after a few seconds it gets stuck at some message like "ACPI Error yadayadasomethingsomething" (not close to that computer right now so I can't quote it fully).

What I've found when Googling is basically just people saying that one should try to install with acpi=off. Is there any danger in running Ubuntu with this on a daily basis? 
Also, how do I add this acpi=off parameter when installing from a bootable USB-stick?

I'm a complete noob when it comes to Linux and Ubuntu, all I know is how to compile Android from source, which is also mainly what I use Ubuntu for.

Appreciating any kind of help!

---

### Post by oldfred on 2012-09-07
I do not know about ACPI, but with nVidia you also (or instead?) will need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes settings in BIOS can make a big difference also.

---

### Post by fritzhy on 2012-09-07
> **oldfred said:**
> I do not know about ACPI, but with nVidia you also (or instead?) will need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes settings in BIOS can make a big difference also.

Okay, so there's no way to make these pre-installation changes when installing from a pendrive?

I think it's very weird (and annoying) that this is happening, guess I should try some other installation methods... Would very much like to solve it.

---

### Post by fritzhy on 2012-09-07
Update: Managed to find a way to apply the acpi=off parameter and the install went fine. Not quite sure what kind of warning signals I should be looking for now thoug, if it even affected anything. I didn't have to use the parameter when rebooting anyway, so it might've just needed to be off when booting from the drive.

---

