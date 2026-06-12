---
title: "USB boot install Ubuntu 16.04 LTS  --&gt;  blackscreen issue"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by lodrik on 2017-02-17
Hey Guys,

I'm desperately trying to install Ubuntu 16.04 via a Live CD (USB) as a dual boot on my machine, but no matter what I try I run into a black screen after choosing "Try Ubuntu without installing" or "Installing Ubuntu" in the boot menu. Please help me fix this issue :)



**Error Message:**
The problem is that I don't even get any error messages at all. I can enter the boot menu and select my USB-stick just fine. Then I'm in the screen where I can choose what to do, for instance "try out Ubuntu live", "install ubuntu", "etc", and I can also change the boot parameter. When I try the "try-out" option or the "install option" I get a pink Ubuntu loading screen for a few moments, followed by a black-screen. At the black-screen state I can't do anything anymore and have to hard-restart my computer.



**What I already tried:**

1. I tried several USB sticks and several programs to create a Live USB stick (for instance: Rufus, Universal USB Installer, ...). Moreover, I tested the USB sticks on different machines, and there they worked just fine.

2. I changed the boot parameter from "quite splash" to "nomodeset", "acpi=off" and "nolapic". Nothing worked so far.

3. I tried using "UEFI" boot mode, as well as "UEFI + Legacy" boot mode. --> Nothing changed.

4. I tried USB2 ports, as well as USB3 ports. --> No luck

5. I tried connecting to my monitor with a Display Port, Mini Display Port and HDMI cable.  -->  No luck  [No DVI/VGA connection available]




[B]Setup:

[/B]I have 3 drives: C:\  -->  NVMe SSD,  D:\  -->  SSD,  E:\  -->  HDD.

On the C-drive I have Windows 10 installed, and I would like to install Ubuntu on the free partition on my SSD (D-drive). I already resized and freed space on the partition: 

[ATTACH=CONFIG]273765[/ATTACH]




[B]System Specs:
[/B]
- Motherboard: X99A SLI PLUS(MS-7885)
- Chipset: Intel X99
- BIOS: 1.D0 (up-to-date version, flashed already)

- Boot mode: UEFI  (also tested in UEFI + Legacy, but same error)
- Fast Boot: disabled
- Secure Boot: disabled

- Monitor:  ROG PG279Q  [only HDMI or Display Port connection, 1440p]

- GPU:  GTX 1080, up-to-date driver installed
- NO integrated onboard graphics on motherboard (!)

- CPU:  i7-5820K  (overclocking disabled for the installation)




**Others:**
For performance and stability reasons a "Wubi install" of Ubuntu is not possible for me



Thanks in advance for your help :)

Lodrik

---

### Post by oldfred on 2017-02-17
Wubi does not really exist anymore. Last version was 12.04 which is obsolete in a couple of months. And 12.04 will not support new systems.

You should just need nomodeset until you install the proprietary nVidia driver. 
Ubuntu repository may not be quite new enough and you then should use ppa.
The issue may then be you need nomodeset plus another boot parameter or two?

Only use Something Else install option with multiple drives. That is the only way you get to choose partitions and more importantly which drive to install grub2's boot loader into if BIOS install. With UEFI choice does not work, it only installs to sda's ESP.

UEFI install also has issues with anything more than one drive. 
Grub only installs to the ESP - efi system partition on drive seen as sda. While NVMe drives are supported there are posts where grub seemed to have issues installing to ESP when a partition on NVMe drive.
But if Windows is in BIOS boot mode, better to have Ubuntu in BIOS/CSM/Legacy boot mode.

But if Ubuntu on its own drive, I still suggest using gpt and making first partition an ESP, FAT32 100 to 500MB for future use with UEFI, and second partition 1 or 2MB unformatted with bios_grub flag, for grub to correctly install in BIOS boot mode on gpt partitioned drives.

Lack of internal video may make it more difficult.

Have not seen many X99 motherboards.

Often issues are common by brand since same UEFI often used with just modifications for specific features.
One of these may have more info?
 MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
[http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot](http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot)
MSI-Z97/Intel's Core i7 5775C Broadwell Is Running Well On Ubuntu 15.10 Iris Pro 6200
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
MSI Z170
[http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095](http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095) 

      
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

