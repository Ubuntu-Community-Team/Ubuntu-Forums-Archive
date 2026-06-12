---
title: "Install can't see HD"
date: 2018-10-20
forum: Installation &amp; Upgrades
---

### Post by nul2 on 2018-10-20
I am trying to install Ubuntu and when I boot from the USB I get to the window that asks where to install and all it sees is the USB. When I boot into Ubuntu on the USB I can see the HD in the terminal. I am really new and this might be something simple, but I don't know how to install Ubuntu at this point.

---

### Post by oldfred on 2018-10-20
What brand/model system?
What video card/chip?

Many need UEFI update and if SSD need firmware update.
Some like Dell need you to change UEFI drive setting from RAID or Intel SRT to ACHI. But if booting Windows add AHCI drivers first into Windows.

Post this from live installer:
sudo parted -l

---

### Post by nul2 on 2018-10-20
The brand it HP H8 1414. AMD 3.4 with 10 GB of ram.  [https://support.hp.com/us-en/product/hp-envy-h8-1400-desktop-pc-series/5295996/model/5296860/document/c03517389](https://support.hp.com/us-en/product/hp-envy-h8-1400-desktop-pc-series/5295996/model/5296860/document/c03517389)
I can boot from the USB. Is there a way to install from the terminal? I can see the drive once I'm in the USB.

---

### Post by oldfred on 2018-10-20
Have you updated UEFI?

Issues often common across many models of same brand as same UEFI, with some different options. More difference if Intel or AMD by same brand.
       Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
      
 HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227) 
    
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
      [/URL]
 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 
    [URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

### Post by nul2 on 2018-10-22
[COLOR=#000000]I answered my own question. I finally got it to install on the hard drive. It turns out that I had to format it in the disks app and change the format to ext4. There was a lot of windows stuff left on it. After formating the drive it all worked out. I guess its the growing pains of learning a new OS. Thank you for your help.[/COLOR]

---

