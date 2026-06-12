---
title: "Ubuntu dual boot with windows 10 problem"
date: 2017-12-23
forum: Installation &amp; Upgrades
---

### Post by abhishekchaturvedi on 2017-12-23
Hi,
 I have been trying to install ubuntu 16.04 in dual boot mode with Windows 10 (which came installed on the Alienware R7 desktop that I recently bought). 

Windows is installed with UEFI. 

To install Ubuntu I had to disable Secure Boot, and change the SATA Option in Bios settings to use AHCI (from RAID) for the installer to detect the drives. After the installation was complete, I couldn't boot into Ubuntu. (I can still boot into Windows after changing the Sata Option back to "Raid", but that's not important as I want to use Ubuntu as my primary OS). 

I followed the instructions to fix the boot issues using "Boot-Repair" using "Recommended options", but it doesn't seem to fix the issue -- i.e., after reboot I am still not able to boot.

I can't boot into Ubuntu at all, as grub menu doesn't even show up. I created the report using Boot-Repair here ([https://paste.ubuntu.com/26242417/](https://paste.ubuntu.com/26242417/)). I'd really appreciate if someone can please shed some light on what am I doing wrong. 

Really appreciate the help.

Thanks.

---

### Post by oldfred on 2017-12-24
While booted in Windows install the ACHI drivers, so you can boot both systems in AHCI mode.

Was RAID on when you ran report?
It does not show Ubuntu installed at all, and only seems to show flash drive.

Is drive SSD and newer NVMe?

Many Dells (Parent Co of Alienware), have had to update UEFI and update firmware for SSD.
       Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr
      [/URL]
 Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488) 
    [URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]

[/URL] [https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

