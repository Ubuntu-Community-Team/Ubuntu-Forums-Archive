---
title: "Installing Ubuntu to Existing Acer XC-704 (Windows 10)"
date: 2020-06-22
forum: Installation &amp; Upgrades
---

### Post by brucethedog on 2020-06-22
I have installed Ubuntu to many laptops before, including dual boot options, but attempted the other day to install to a Windows 10 Acer XC-704, which is 2 years old, and has 1 3Tb drive currently.

I booted off a USB stick and was able to set up the install to use 200Gb of that drive.

After the install (no errors), everytime I reboot, it just goes into Windows, theres no GRUB with Ubuntu option.

Anyone else had similar issues?

D

---

### Post by yancek on 2020-06-22
You indicate you have windows 10 but do not say whether it is a pre-installed, default UEFI install?  Is it?  Ubuntu has had a site online at the link below for several years which specifically explains dual booting with windows 10 UEFI.

Most new Acer computers require that a user set  a Supervisor  password in the BIOS and then enable Trust before being able to boot/install another OS.  Have you done that?  I don't use Acer but you might do an online search for the manual for your specific Acer.


 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by brucethedog on 2020-06-22
Yancek thanks for your response. I'll check out the documentation but looks like its UEFI, the original OS may have been Windows 8, I got the machine from a relative, and have upgraded to Windows 10 since.
If I use Disk management tool on Win10, I can see the partition that was in the attempt. I guess I can delete that, and try and get this UEFI BIOS to allow another OS on it and reattempt?

---

### Post by CelticWarrior on 2020-06-22
Basically, how it boots is how it installs. So, you need to assure you're booting in UEFI mode. Then you can use Gparted in a live session to mange the partitions.

Important: Before any of that disable Fast Startup in Windows.

---

### Post by brucethedog on 2020-06-28
Hi got this working thanks all.
in the end I had to open an elevated Cmd in windows and enter
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

after that grub menu appears on reboot and I can choose Ubuntu or win10

i took backups beforehand

---

