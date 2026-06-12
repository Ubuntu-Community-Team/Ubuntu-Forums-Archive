---
title: "Ubuntu 12.04LTS, windows 8 dual boot"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2014-03-06
Some time ago I got a Lenovo laptop with win8 preinstalled.  I installed Ubuntu 12.04 LTS but kept the windows partitions.

However, the system no longer booted into windows 8, throwing an error that the hardware had changed.  I was not too concerned as I (almost) never need windows.

Well, now I need windows.

I started messing with the laptop, and discovered that, if I enter the grub menu by pressing 'c' and then at the grub prompt

ls (hd0,gpt2)
exit

the laptop boots into windows 8 perfectly.  This is repeatable; I've done it twice now.

This qualifies as a total WTF as I have no clue why it would do this, but it tells me that windows 8 is fine on the machine and the problem is with the grub chainloader.

I have it in windows; as soon as I get the password from my kids I will create a recovery stick, but in the meantime how do I get this fixed permanently?  What is the correct grub invocation for chainloading lenovo windows 8?

---

### Post by cpdondo on 2014-03-06
I think it's a buggy bios....  If I set the bios to UEFI it boots windows; if I set it to legacy it boots into Ubuntu.  Since I'm probably going to boot into windows once a year this works for me.

---

### Post by oldfred on 2014-03-06
No, that is exactly how UEFI/BIOS works when you have one system installed in UEFI mode and the other system in BIOS boot mode.
UEFI and BIOS are not really compatible and you cannot change boot mode after you start booting. Or you cannot use grub to change mode since you already started in BIOS mode.
But you can choose from UEFI and some systems will auto switch and you can use the one time boot key.

You can also convert Ubuntu to UEFI boot by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI). Usually easiest with Boot-Repair. Then you can dual boot from grub menu if both are UEFI. 
But do not then turn on secure boot as that is another change.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by cpdondo on 2014-03-07
A quick summary of the solution:

1.  The Lenovo IdeaPad S405 will not boot from a USB CD.  Not.  You need a USB stick.  Download the boot repair iso, and create a bootable USB stick.

2.  In windows, turn off hibernation on shutdown.

3.  In the bios, turn off secure boot and turn on UEFI.

4.  For the Lenovo, turn off the laptop and push the OneKey button (on the side next to the power button) to get the boot menu.

5.  Boot from the USB stick and follow instructions.

On mine, boot repair created 5 different windows entries, only 2 of which booted, but that's OK.  I edited the files in /etc/grub to get rid of the ones that don't boot and renamed the rest to make more sense.

---

