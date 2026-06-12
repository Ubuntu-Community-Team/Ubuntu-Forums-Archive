---
title: "Installing Ubuntu 16.04 on Dell XPS 8910"
date: 2017-02-08
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2017-02-08
Hello guys


I'm Struggling a lot trying to install Ubuntu 16.04 in a DELL XPS 8910 Workstation. Do you know if there is any guide to install it?

[COLOR=#111111][FONT=Ubuntu]For example during the installation i receive this error: executing grub-install /dev/sda failed

The problem is the NVMe ssd disk?[/FONT][/COLOR]

---

### Post by oldfred on 2017-02-08
While they updated Linux to support NVMe drives, grub in UEFI mode seems to want to only install to sda.
But you need it to install to /dev/nvmen1p1, if first  partition is the ESP - efi system partition. Or perhaps just the drive like nvmen1  as with install to sda, we do not specify partition but with UEFI it knows to put boot files in the ESP.
Some have had it work, but others have had issues, so not sure if some very new versions of grub have been updated or not.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

One user with a Dell laptop, mentioned it boots from /EFI/Boot/bootx64.efi. That is a fallback or hard drive boot entry. It can be used for internal drives but is the file/location that all external drives boot from in UEFI mode. Boot-Repair will copy /EFI/ubuntu/shimx64.efi to be bootx64.efi if you check in advanced mode the "use the standard efi file" option. If you then already have some type of entry saying UEFI:hard drive or similar (not ubuntu entry) you may be able to boot.

---

### Post by giobaxx on 2017-02-09
Tanks a lot for the Help. Yesterday i Solved the problem. First I have Dowloaded the Distro 16.04.1. With this distro i was able to run the Live Version of Ubuntu. With the Distro 16.04 was impossible also run Ubuntu in live Version due to the coninuous error i received at screen. Then i have Create a first partition of 500 MB with EFI, and then the rest of the partitions for the system.

At the moment seems to WORK!!!:p

---

### Post by oldfred on 2017-02-09
You can change to [Solved].

Dell often released its new drivers needed for new systems, but it can take a while for those changes to be included in a distribution, kernel updates & support software.

---

