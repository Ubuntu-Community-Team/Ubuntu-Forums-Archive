---
title: "Asus k501ux- Ubuntu will not install or run from usb."
date: 2016-03-08
forum: Installation &amp; Upgrades
---

### Post by kyleh583 on 2016-03-08
Hello, I'm trying to install Ubuntu on my laptop as a dual boot with windows 10. When I select boot from USB this page comes up:
[IMG]https://goo.gl/photos/S7WPkDJ4erCKsd7s9[/IMG]
After that when I click either Try Ubuntu without installing or Install Ubuntu, it scrolls through a bunch of error statements (I think).
[IMG]https://goo.gl/photos/BTKVu89doCHG61zb8[/IMG]
Then it usually hangs at this, if not here then somewhere else:
[IMG]https://goo.gl/photos/BWf467AUpKQkqUkZ8[/IMG]

I have successfully installed ubuntu on my dell laptop which is also windows 10, with UEFI and secure boot on. When installing on my dell laptop I got the same exact first page and I also did not notice a page full of 'errors'.


Can anyone help me with trying to get Ubuntu installed? Thanks



Here are some short specs on my Asus:
Operating System
 Windows 10 Home 64-bit
CPU
 Intel Core i7 @ 2.50GHz 96 °F
 Skylake-U/Y 14nm Technology
RAM
 11.0GB Dual-Channel DDR3 (11-11-11-28)
Motherboard
 ASUSTeK COMPUTER INC. K501UX (U3E1) 101 °F
Graphics
 Generic PnP Monitor (1920x1080@60Hz)
 Intel HD Graphics 520 (ASUStek Computer Inc)
 2047MB NVIDIA GeForce GTX 950M (ASUStek Computer Inc) 97 °F
 ForceWare version: 362.00
 SLI Disabled
Storage
 232GB Samsung SSD 840 EVO 250GB (SSD) 83 °F
 238GB Hitachi HFS256G39MND-2300A (SSD) 85 °F
Optical Drives
 No optical disk drives detected
Audio
 Conexant SmartAudio HD

---

### Post by oldfred on 2016-03-08
Do you know if booting with Intel or nVidia video?
Or can you set that in UEFI?
If nVidia you may need nomodeset, but if Intel you may need one of the Intel options.
And some laptops need one or more other ACPI related boot options.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 
    Graphics Resolution- Upgrade /Blank Screen after reboot
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) 
   # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 

Other Asus, but may have similar UEFI settings:

 Asus M32CD desktop - Skylake several boot parameters required
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

---

### Post by gordintoronto on 2016-03-08
What version of Ubuntu? Generally, if the motherboard is newer than the OS, it can be very frustrating.

---

### Post by marco130 on 2016-03-09
I have that same laptop.
You'll have to install ubuntu 15.10
1.download the ISO.
2.drag the files from the ISO directly to a USB drive.
3 restore BIOS to its default settings. You will install it in UEFI mode doing an EFI partition
4 plug the usb and restart windows, then you will press continuously esc till it shows you the boot menu and then you choose your usb drive.
5 when the ubuntu installer asks you what to do. you have to choose do something else.
6 do at the end of the drive an efi partition of 535 MB, a swap, /(root) and home partition manually, all at the end of the drive  ( I installed on this laptop a hardrive, so I have windows on the ssd, game in 320 gb in the hard drive and linux in 150 gbs) I divided it this way ( 50GB for root, 100 gb for home and 4 or 3 for swap + 535 for efi partition)
7 after you finish installing the OS go to the bios menu and choose the boot manager of your preference.
9 choose start in recovery mode and then fix the packages, then resume
8 to enable wifi copy and paste this on the terminal
echo blacklist asus-nb-wmi | sudo tee -a /etc/modprobe.d/blacklist-asus-nb-wmi.conf
9 you must upgrade linux to the latest kernel so that you can be able to use the OS
10 thats it, backlight wont work and I still have 2 errors before the os starts that I don't know how to fix.

I hope this helps you. if you have any issue PM me.

---

