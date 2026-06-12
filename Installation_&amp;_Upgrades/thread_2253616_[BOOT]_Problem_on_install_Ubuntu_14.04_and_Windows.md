---
title: "[BOOT] Problem on install Ubuntu 14.04 and Windows 8.1"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by m0rd0r on 2014-11-21
Hi all,

I have a Toshiba SATELLITE L50-A-1EL notebook with pre-installed Windows 8.1 operating system. I'm trying to install Ubuntu 14.04 on it but I fail.
I disabled the Secure Boot option in BIOS and disable the "fast boot" on Windows 8.1 (enabling complete shutdown of my notebook).

With a DVD/USB image of Ubuntu 14.04 in my notebook I'm able to get the (EFI) GRUB loaded at start-up and I can chooce to start the operating system
(the BIOS is configured with UEFI support).

After that, the screen of my pc became blank and it seems to be freeze (it doesn't respond to any pressed key); I can only reboot the notebook.

I try to disable UEFI support in BIOS (the other choise is CMF) and I got the standard ubuntu installation menù (the NON UEFI installation menù). The system starts correctly and I'm able to install Ubuntu in legacy mode (but the bootloader is installed in /dev/sda partition and not in /dev/sda2 where is locate the EFI boot).

With this configuration I'm able to start Ubuntu if my BIOS is set-up in legacy and Windows 8.1 if my BIOS is set-up in UEFI mode.

At start-up I can't choose Ubuntu or Windows at the same (because the legacy grub see only Ubuntu and UEFI see only Windows).

Question:
  - how can I solve this issue?

Best Regards.

---

### Post by yancek on 2014-11-21
I'm not sure how to remedy your situation as I don't use UEFI myself.  From everything I have read, if windows is installed in UEFI mode then you must install Ubuntu UEFI or the result will be what you get.  Either one or both systems unbootable or you need to make the change in the BIOS on each boot.  You need to find the option to install Ubuntu in UEFI and then it will put its efi files on the same partition on which windows has its efi files.  You might read the link below?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-11-21
Be sure to fully back up Windows and make a Windows repair flash drive.
Use Windows to shrink its NTFS partition and immediately reboot so it can repair to its new size. May sure fast boot is still off as Windows likes to reset to its defaults. 
Do not create any partitions with Windows.

 [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by m0rd0r on 2014-11-22
Hi all,

using an Gnome Ubuntu USB image I was able to install linux on my notebook. Now I have a problem. At startup the grub loader is not called but Windows is started. I created a rFind USB image and running it at start-up I saw the ubuntu entry. Selecting the EFI entry I got GRUB menu and selecting UBUNTU I can enter in my installed ubuntu o.s.  (now I'm writing ith linux).

Question:
- how can fix my siituation to run GRUB at startup and not use every ttime the USB flash with rFind ?

Thanks a lot.

---

### Post by ubfan1 on 2014-11-22
You could use efibootmgr to add a nvram boot entry for Ubuntu if you don't already have one.  efibootmgr can also change the boot order, so grub is first (since it might be present, but not in first boot order).  If present, you should be able to select it with the function key at power on (varies by machine) to select ubuntu, or maybe hdd then ubuntu.

---

### Post by oldfred on 2014-11-22
I think Toshiba's also need one of the work arounds. 

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Most seem to use this option if dual booting. In efi partition:

  Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  
Then boot harddrive entry in UEFI menu. You should be able to set it to default in UEFI or with efibootmgr.

If grub has a major update you may have to copy the newer grubx64.efi again.

---

### Post by m0rd0r on 2014-11-25
Hi,

I will try one of the work-around that you suggest me.

---

### Post by m0rd0r on 2014-11-26
Hello everyone, I am able to solve my problem following the instructions in:

[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Thanks a lot.

---

