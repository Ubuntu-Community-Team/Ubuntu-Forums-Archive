---
title: "Installation of Ubuntu 16.04. dual boot  ---- with MSI GE73 7RD Raider (GTX 1050 Ti)"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by ant90 on 2017-12-09
Hello All,

I have recently bought a GE73 7RD Raider Laptop from MSI with preinstalled windows. To install Ubuntu 16.04 alongside windows10, I have disabled FastBoot, Intel Speedstep, SecureBoot in BIOS (boot mode - UEFI). Initially, Ubuntu installation was getting stuck in the installation progress screen and I could not go further. Then I added following grub parameters (with key 'e' over 'install ubuntu'): nomodeset and libata.force=noncq (as per [http://www.archive.ricston.com/blog/installing-ubuntu-14-04-3-windows-8-1-dual-boot-msi-ge72-2qd-apache/](http://www.archive.ricston.com/blog/installing-ubuntu-14-04-3-windows-8-1-dual-boot-msi-ge72-2qd-apache/) ).

I could successfully install ubuntu on my SSD. I logged in to Ubuntu, and then installed Nvidia drivers ((GTX 1050 Ti)) (sudo add-apt-repository ppa:graphics-drivers/ppa sudo apt-get update sudo apt-get install nvidia-384 nvidia-settings). After the restart, PC got stuck at the login loop. I have then tried to install intel graphics (sudo apt-get install xserver-xorg-video-intel) in the terminal (Ctrl - Alt - F1). 

Now the pc is stuck at /dev/sda6: clean, ###/## files, ##/## blocks. Any help would be greatly appreciated

---

### Post by oldfred on 2017-12-09
Sounds like you did everything right.

I have seen some with newer Dell with NVMe SSD, have to both update UEFI and update firmware for SSD.

Are you able to boot with recovery mode?
And/or remove quiet splash to see if boot process is continuing and where it stops. May also be in log files.

Some older MSI, often issues are common by brand, then models.
       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by mankeulv on 2017-12-19
Quick question... Did your touchpad work through the setup? Mine doesn't, and I'm not sure if it's a software or hardware problem...

---

### Post by oldfred on 2017-12-19
I do not have MSI, nor any system with a touchpad.
(my old laptop had one, but I hate them, and immediately install a mouse.)

Did any of the links above with users with MSI systems mention that issue?

---

### Post by mankeulv on 2017-12-19
None of the links I've read has mentioned any problems with the touchpad in this laptops. I've ordered a replacement, will let you guys know if the problem was a faulty unit.

---

### Post by mankeulv on 2017-12-26
Okay, so in response to my previous message, the unit was faulty and I got a replacement. Just letting you guys know.

---

