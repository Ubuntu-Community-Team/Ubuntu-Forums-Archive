---
title: "Cannot install Ubuntu 19.10 to HP Spectre x360 (2020)"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by manziscw on 2020-04-05
Hello,

Today i bought a spectre x360 (2020 Edition) from HP. I Tried to install ubuntu. 
The Livesystem worked after adding nvme_load=YES to the kernel.
I am also able to install it from the livesystem, However after it finished i tried to reboot my Laptop and... in the EFI Partition there is no ubuntu efi file.

The Strange thing is that if i boot from livesystem again, ubuntu can indeed see the files.
i solved this problem by copying that efi files from the livesystem to a usb stick, bootet up Windows and copied the File from the usb stick to the EFI Drives there.

Okay. First thing resolved. But there is another Problem: my Livesystem says that Partition 5 on the NVMe Drive ist ext4 (with the ubuntu installation).
However the grub bootloader in the EFI Partition cannot see that ext4 System and Windows says that the Space on the Disk is Empty and not used.

How can that be?

Some Specs about the Laptop:
HP Spectre x360 (2020 Edition) 13-aw0020ng
with Intel Optane 32GB
Disabled Secure Boot in UEFI-Bios

Many thanks for all replies in advance
Manziscw

---

### Post by oldfred on 2020-04-05
A lot of threads on HP 360, not sure how different models may be.
But issues often common by brand across multiple models.

HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
HP X360 Update UEFI F20
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by manziscw on 2020-04-05
Thanks for the hints. I read a lot of articles but none of them worked for my problem.

The Link with disabling Intel Optane sounds promising, maybe that could solve my Problem. I will look into it.

It is very strange that ubuntu live says that there are files on the NVMe but the UEFI and Windows says there are no file there

Thanks and Greetings

---

### Post by manziscw on 2020-04-05
Thanks for the Help, after disabling OPTANE it worked fine.

So for all with the same Problem:
1) Boot Windows
2) Start the Intel Optane Memory tool
3) disable Intel Optane
4) Install Ubuntu
5) have fun :)

---

### Post by oldfred on 2020-04-05
Glad you found solution.

Some worry about turning off optane.

Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

