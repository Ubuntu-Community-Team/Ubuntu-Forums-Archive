---
title: "Help to install on ssd with gpt, boot with efi via grub2"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by varx on 2011-08-12
As I now have a 120Gb SSD in an efi-capable laptop, I'd like to re-install 11.04. I'd like to format the SSD as gpt and make it bootable with efi. And I'd like to use grub2 as the bootloader.

Can anybody walk me through this? I'm pretty new to Ubuntu, though I've used several other distros for a number of years. When I last installed 11.04, I don't remember seeing options for gpt, for example. And I don't know how get things booting with efi.

Thanks very much.

---

### Post by YesWeCan on 2011-08-12
My first thought is why would you want to do this, but I'll assume you have a good reason.

I believe that efi support by Grub is still in the experimental stage.
Grub can be used in a GPT in bios boot mode. You need to make a bios boot partition for it to install its main program to and it will put boot code in the protective MBR. You can boot a live CD/usb and use Disk Manager to format your SSD with a GPT and make all the partitions before you install.

---

### Post by varx on 2011-08-12
> **YesWeCan said:**
> My first thought is why would you want to do this, but I'll assume you have a good reason.

I believe that efi support by Grub is still in the experimental stage.
Grub can be used in a GPT in bios boot mode. You need to make a bios boot partition for it to install its main program to and it will put boot code in the protective MBR. You can boot a live CD/usb and use Disk Manager to format your SSD with a GPT and make all the partitions before you install.
Thanks for the info, YesWeCan. 

I've been using an older machine for a number of years, and now that I've got this new one, I want to put its capabilities to the test. Even though I don't expect to be using a 2Tb+ drive anytime soon, it looks as if gpt is going to become standard, especially since it's part of the UEFI initiative which new motherboards seem to be supporting.

I'm interested in trying efi for similar reasons. 

I'm wanting to go with grub2 because it will likely supplant grub and because it's geared to work with gpt. 

But what's really motivating me is probably the old George Mallory-Mt. Everest thing,  applied to a wannabe geek.

---

### Post by YesWeCan on 2011-08-12
Go for it!
This may help the intrepid explorer :)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by srs5694 on 2011-08-12
You don't see GPT options in the Ubuntu installer because there are no options you can set. The Ubuntu installer gives you no choice in the matter, but will use either MBR or GPT under different circumstances:


[list]
[*]If a partition table exists on the disk, the installer uses it as-is. This is your way to force it to use a particular partition table type.
[*]On a BIOS-based installation with a completely blank disk, Ubuntu uses MBR on smaller disks and GPT on larger disks. I don't know precisely where the cutoff point is, but it's somewhere between 1 TB and 2 TB.
[*]On a UEFI-based installation with a completely blank disk, I'm pretty sure that Ubuntu always uses GPT no matter what the disk size, but I'm not 100% positive of that.
[/list]


In my experience, the Ubuntu installer's operation in UEFI mode is a bit flaky. The worst problem is that it puts a fresh FAT-16 filesystem on the EFI System Partition (ESP), even if the ESP had a suitable filesystem on it to begin with. This has the effect of wiping out any existing boot loaders, and because Windows 7 seems to expect a FAT-32 filesystem on the ESP (as per the UEFI specification), it makes it harder to install Windows 7 after installing Ubuntu. On a completely blank disk, Ubuntu also creates an ESP that's rather small -- usually in the tens of megabytes. This is a problem because at least one boot loader ([ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom)) is most easily configured if your kernel and initial RAM disk are in the ESP, and the ESP that Ubuntu creates is too small for this. IMHO, an ESP of ~200-250 MB is a good size.

IMHO, the best way to proceed is as follows:


[list=1]
[*]Using an emergency disk or Ubuntu in "live CD" mode, use GParted, parted, gdisk, or some other tool to create your partitions, or at least the basic GPT data structures and two partitions:

[list]
[*]A ~200-250 MB ESP. Put a FAT-32 filesystem on it, although depending on how you install, that may be wiped out. If you've already got Windows or some other OS installed, keep the existing ESP (but enlarge it to at least 100 MB, if it's smaller than that).
[*]A ~1 MiB [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition). You might not use this at all, but depending on how you install, it might be necessary on a temporary basis.
[/list]

[*]If Windows is already installed, back up the ESP. An ordinary file copy to another partition or a USB flash drive will do the job; there's no need to worry about boot sector code or the like.
[*]Install Ubuntu. You can do this in either of two ways:

[list]
[*]In UEFI mode -- This will wipe out the ESP, which at this point won't be a problem if no other OS is installed; but if another OS is installed, you'll need to restore its files from the backup after you install Ubuntu.
[*]In BIOS mode -- This will use the BIOS Boot Partition and render Linux bootable in BIOS mode. After you install in this way, you can switch to UEFI mode booting by installing a suitable boot loader (GRUB 2 or ELILO) in the ESP and switching the firmware to boot in (U)EFI mode.
[/list]

[*]Adjust or re-install your ESP and boot loader configuration, depending on the installation method.
[/list]


Note that if you install in UEFI mode and select the "other" partitioning option (to partition manually), you must explicitly flag the ESP as such (IIRC, the Ubuntu installer calls it an "EFI boot partition" or some other not-quite-standard term). You don't explicitly set a mount point, but it'll end up being mounted at /boot/efi when you're done.

---

### Post by varx on 2011-08-12
@YesWeCan: Thanks for the helpful link, and thanks for the encouragement. I'll probably end up stuck in an ice crevice, but at least I can say I tried.

@srs5694: This is just the kind of info I was looking for. Thank you *very* much.

Now I'm thinking I'll call in sick one day next week. Monday's generally a good day to come down with something. :)

---

### Post by varx on 2011-08-12
@srs5694: FYI, I don't need to try to dual boot with Windows. This is a Linux-only rig, which simplifies things.

---

