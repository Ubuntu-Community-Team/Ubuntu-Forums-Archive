---
title: "Does &quot;erase disk&quot; erase all drives?"
date: 2020-02-11
forum: Installation &amp; Upgrades
---

### Post by thirstywater on 2020-02-11
Hello! Made a few mistakes trying to install dual-boot with windows 10, decided to start over, starting with Ubuntu. When installing, does "erase disk" option erase all drives or only the drive that Ubuntu will be installed on?

---

### Post by oldrocker99 on 2020-02-11
Always install Windows **FIRST!**. When you install Linux, it will create a boot sector which will boot either OS . Installing Linux first will result in Windows overwriting the Linux boot sector.

Once you have Windows installed, you can select "Something Else" at that screen.

This is a better guide than I can come up with from then:
[https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/](https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/)

---

### Post by Impavidus on 2020-02-12
If you have multiple disks, the "erase disk" option should only wipe the disk you install Ubuntu on, but it's a bit hard to predict which disk that will be. With multiple disks, it's best to use manual partitioning ("something else"). If you have only a single disk, then "erase disk" will erase that disk.

Keep in mind that "disk" refers to the physical device you plug into your computer (or was plugged into it in the factory). Most laptops and many desktops have only one. Many new Linux users are confused by Windows' confusing terminology, as Windows calls a partition a disk too. It's only part of one. The "erase disk" option will erase all partitions one one of the disks.

And indeed, it's best to install Windows first. The Windows installer has a tendency of wiping Ubuntu, or at the least making it unbootable. Ubuntu is friendlier to other OSs it finds on the system.

---

### Post by guiverc on 2020-02-12
I recently did QA-test installs of 18.04.4 flavors (Lubuntu, Xubuntu, Kubuntu) on hardware, of maybe 36 installs onto machines with more than 1 drive, on only 3 was I unsure of which drive it was installing to.

I'm hardly a beginner, and with QA-tests I just follow instructions; it did exactly what the Quality Assurance tests required me to do, but that's still ~8% where I was somewhat unsure of what would occur (an option I'd not use in real life; I'd always use "Something else", "Manual Partitioning" or "Manual" to avoid any uncertainty as stated by prior responses). 

 In no cases did it erase any other disk than the drive it was supposed to, however with the risk of uncertainty on some options (possibly just wording), it's just better to be safe than sorry.  Read what the other responses have said, use "Something else" or "Manual".., don't forget disk means all the disk (thus all partitions), and if unsure which disk (*or it's hard to select which drive*), back-out & use "Something-else/Manual.."

---

### Post by P-I H on 2020-02-12
My understandings are these with installs in UEFI mode and systems with several disks:
When you use "Erase disk and install Ubuntu" you will get a drop down menu where you select the disk to use. When I'm unsure I use the program Disks to understand the configuration. 
Grub always installs in the first disk, sda or nvme0n1.

With an UEFI install it doesn't matter if you install W10 or Ubuntu first. On this system Ubuntu is installed first. W10's boot file is installed in the existing EFI file.

This system is a triple boot with sda (Ubuntu 20.04), sdb (W10) and sdc (Fedora 31).

When you start Ubuntu after the W10 installation and run sudo update-grub, you will get a grub menu with Ubuntu and W10.

---

