---
title: "Ubuntu 11.10 b2 Install - Install succeeds, but no GRUB after install"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by OrphanShadow on 2011-09-23
Hi all

I installed the 11.10 beta 2 today, dualbooting with an active Windows 7 partition.

The machine is a Lenovo S205 Ultraportable. Specs:

AMD E-350 Dual Core APU w/AMD Graphics
3GB DDR3
320GB HDD

Booting to the LiveUSB and installing the system went fine. Upon reboot, however, the machine boots straight into Windows. No Grub prompt or anything.

I've checked the hard drive structure and it appears all the Ubuntu partitions are correct (80GB Ubuntu, everything else Windows). I also did not use any special install instructions.

Any ideas as to why this is happening?

(I can give any more machine information as required)

---

### Post by OrphanShadow on 2011-09-23
Just to add an update to this:

I have discovered through google searches that the system I own utilizes UEFI instead of a traditional BIOS system.

In light of this, I made sure that I had the latest UEFI installed, and attempted to install the Beta again.

Same situation: Installs with no visible errors, then upon reboot it still boots straight into windows, no grub screen or anything. Its as if Ubuntu isnt even there.

Is this likely to be an issue with Ubuntu's default installation location for Grub? (Or, in this case, Grub-EFI?) Or something else entirely?

Thanks in advance

---

### Post by Quackers on 2011-09-23
Try doing a search for uefi installation. There have been a couple of threads about it fairly recently.

---

### Post by OrphanShadow on 2011-09-23
Well having expanded my search scope I came across an interesting section in the Arch Linux Wiki:

[https://wiki.archlinux.org/index.php/GRUB2#For_non-Mac_UEFI_systems]("https://wiki.archlinux.org/index.php/GRUB2#For_non-Mac_UEFI_systems")

Its goes into great depth in the matter and how to get it working. I havent been able to put it into practise yet though, want to wait till I have access to another computer as a backup xD

This is probably stuff that should work out of the box though =/ Or maybe its just that I have a unique setup.

---

### Post by srs5694 on 2011-09-23
First, you may want to verify that Windows in fact installed in UEFI mode. You can do this by booting the Ubuntu installer into the live CD mode, opening a Terminal window, and typing the following command:

```

sudo parted /dev/sda print

```

The output should include a line that identifies the partition table type, such as:

```

Partition Table: gpt

```

If that code reads "gpt", as it does in my example, then Windows installed in UEFI mode. If it reads "msdos", though, then Windows installed in BIOS mode. The solution in either case is to properly install a Linux boot loader, but the details of how you do that are *very* different, so it's critical that you do it in the right way.

Assuming you did install in UEFI mode, chances are Ubuntu failed to install its boot loader. This might actually be a good thing, since Ubuntu's installer tends to trash the EFI System Partition (ESP), which is where boot loaders reside. To recover, you'll need to install an EFI-capable Linux boot loader. There are many ways to do this, depending on your needs and preferences. I've recently created a new Web site, [Managing EFI Boot Loaders for Linux,](http://www.rodsbooks.com/efi-bootloaders/index.html) that may provide you with some guidance on the topic.

---

### Post by CyberNeT85 on 2011-10-14
i've got this problem aswell, though, ive got installed the final release of 11.10. I know its installed, because i resized my w7 partition.

---

### Post by oldfred on 2011-10-14
@CyberNeT85
Please start a new thread. Boot issues are almost always unique.
Download this to liveCD or its liveCD and post link to boot script results in new thread. It may repair your system also.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

