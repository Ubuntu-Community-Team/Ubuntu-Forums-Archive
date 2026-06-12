---
title: "Problem booting Ubuntu 16.04 (falling to initramfs)"
date: 2017-06-18
forum: Installation &amp; Upgrades
---

### Post by warudo on 2017-06-18
Hello,

I've been trying to install Ubuntu without success. When I try booting, I get to initramfs:

```
 Gave up waiting for root device. Common problems: - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{My UUID} does not exist. Dropping to a shell!


BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)

```


The UUID in Grub.cfg and the one listed by blkid seem to match. 

My setup is pretty simple, I have Windows 10 installed on sdb. On sda, I have a NTFS data partition and an ext4 partition for Ubuntu.

What else could I check?

---

### Post by ubfan1 on 2017-06-18
Take a look at [https://askubuntu.com/questions/109500/boot-issues-long-delay-then-gave-up-waiting-for-root-device/115524#115524](https://askubuntu.com/questions/109500/boot-issues-long-delay-then-gave-up-waiting-for-root-device/115524#115524)   
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by warudo on 2017-06-18
Thank you for the reply.

I checked the checksums and they match. 

I did a media check on my usb drive before installing and everything seemed fine. 

I am running a memory test right now, but I assume my memory is fine as my Windows install shows no memory problems.

---

### Post by RobGoss on 2017-06-18
Hello and welcome to the forums, You give no information on how you are trying to boot your installation of Ubuntu. 

Were did you get your ISO file of Ubuntu?

What software did you use to create the ISO file?

Are you using a USB or DVD, for the installation?


It's very important to give as much information as possible this will help others help you solve your issue

---

### Post by warudo on 2017-06-18
Fair enough.

I downloaded the ISO straight from the ubuntu website: [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop).

I installed through USB by creating a bootable USB drive with Unetbootin for Windows.

---

### Post by RobGoss on 2017-06-19
I know you stated you're having trouble installing Ubuntu but
what happens when you try to boot in to the Live desktop?

Can you use the live environment for Ubuntu?

---

### Post by warudo on 2017-06-19
Yes, working on the live desktop works. Fairly sure the problem isn't hardware. I changed my setup a bit and I am getting new problems!

I added a new drive and now, I get a grub install error. 

sda is my data hard drive, sdb is my new blank drive for ubuntu and sdc is my windows 10 drive.

Ubuntu tries to install Grub on sda, which fails.

When I try to install manually grub2 on sdb, I get [B]"Installing for i386-pc platform. grub-install: error: failed to get canonical path of 'aufs'"

[/B][COLOR=#111111][FONT=Ubuntu]This puzzles me. [/FONT][/COLOR]

---

### Post by ubfan1 on 2017-06-19
Is Windows installed in UEFI mode?  If you bought the machine from a manufacturer with Widnows 8-10, it is.  If upgraded from Win7, probably not.  In UEFI mode, the installer will only install grub to sda, so that should be the Windows disk, with the EFI partition.  Put another disk there, and put an EFI partition (300-500M, FAT fs) and maybe the installer will use it.  The manual grub should also work putting grub on the device specified, if it has an EFI partition.

---

### Post by oldfred on 2017-06-19
Installing for i386-pc is the BIOS version of grub.
If you have an UEFI system it is grub-efi-amd64.

Is system UEFI or BIOS? 
Are drives gpt which is used with UEFI or MBR which is used with BIOS.
How you boot install media for both Windows & Ubuntu UEFI or BIOS is then how it installs.
So is Windows installed in UEFI or BIOS boot mode?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version in your Ubuntu installer not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by warudo on 2017-06-19
Well, it's a fairly recent PC, so it supports UEFI I believe. However, windows was installed in BIOS compatibility mode as it was originally installed as Windows 7 and upgraded.
All the drives uses a MBR, or should be at least from my understanding.
To install either windows or ubuntu, I boot on a usb drive with the installation files on it.

Right now, I am recovering data because my latest attempt at installing messed up the Windows install.

I am going to install Windows from scratch in UEFI, hoping it will make installing Ubuntu easier.

---

### Post by warudo on 2017-06-19
Hey, thank you oldfred and ubfan1, thanks to you I managed to make it work.

I reinstalled Windows with UEFI and now Ubuntu plays nice with Windows.

Now I'll finally be able to run my damned neural network.

---

