---
title: "Ubuntu 14.04 dual boot Windows 8 UEFI - No Grub"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by Stephen_Fisher on 2014-05-06
Hello,

This is my first time installing Ubuntu 14.04 on a Toshiba S50t-A following the advice in this community (Main guide [here]("https://help.ubuntu.com/community/UEFI") and [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"))
 
Issue: System boots straight into Windows after Ubuntu is installed - No Grub boot menu ever shows up.

System is a [Toshiba S50t-A ]("http://www.toshiba.ca/productdetailpage.aspx?id=2147496275")
Windows 8 pre installed with UEFI

Steps I have taken
1) Fresh install (Back to factory)
2) Completed all Windows 8 updates
3) Updated BIOS 1.70
3) Defragmented hard drive
4) Moved the recovery partition to a USB stick
5) Used Disk Manager to shrink the main windows 8 partition
6) Downloaded Ubuntu 14.04 and main a bootable USB stick (guide [here..]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows"))
7) Disabled Fast Boot under power options in Windows 8
8) Checked under the UEFI that secure boot was disabled and Boot is set to UEFI, Fast boot turned off here as well.
9) Set boot sequence to USB
10) Ubuntu loads - I can choose Try or Install
11) Install 20GB /, 2GB swap, 200GB /home
13) no error in the install
14) on reboot system goes straight to Windows 8

I have used the USB to load ubuntu in try mode and used Boot-Repair with little success or mixed results (only once did I get a Grub menu with Ubuntu only)
see [http://paste.ubuntu.com/7406917/](http://paste.ubuntu.com/7406917/)

What can I do to make this work well? Should I try an older version of Ubuntu or am I missing something, etc. Thank you for your advice.

Stephen

---

### Post by oldfred on 2014-05-06
I thought this meant it was first in boot order, but there are 3 versions. I think it may be secure boot, UEFI, and BIOS but have not seen anything that tells for sure.

```
 BootOrder: 0003,0000,2003,2001,2002
Boot0000* Windows Boot Manager
Boot0001* UEFI: Network Card
Boot0002* UEFI: Network Card
Boot0004* UEFI: HGST HTS541010A9E680
Boot0005* UEFI: General UDisk 5.00
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0003* [COLOR=#ff0000]ubuntu[/COLOR],BootCurrent: 0005


```

Or is that just your installer?
Do you see an ubuntu entry in UEFI menu? Or one time boot key?
It does seem like you did everything correctly.
It does show signed kernels, so you must have installed with secure boot on, or updated with Boot-Repair with secure boot on. Try with secure boot off.

---

### Post by Stephen_Fisher on 2014-05-06
Thanks oldfred. I am in the process of attempting a fresh install once again and will take note of your tip to make sure secure boot stays off.

My UEFI only shows generic boot menu order i.e.. USB, HDD, Network, DVD. It does not show type of OS in the HDD EFI boot area. :(

It would seem I can run Ubuntu fine on the system or Windows 8. Its more of the UEFI not responding well to a GRUB2 boot loader or the implementation of dual. I could just go 100% Ubuntu but I need Visual Studio as a student studying Computer Science.

---

### Post by oldfred on 2014-05-06
Stop!

See link in my signature.
ReInstall with any method other than Something Else may erase drive.

---

### Post by Stephen_Fisher on 2014-05-08
@oldfred Thank you for your help and pointing me in the right direction. LOL -> Stop! See Link in my signature is Gold!. If only I saw it first. I did a fresh wipe and re-install of both windows 8 and Ubuntu 14.04. I made sure secure boot was left on as it gives not issues with my USB install of Ubuntu, or if using Try.

However, Once again the Grub2 boot loader will not show up. Straight to windows 8.

What I have learned is in my UEFI Menu under Choose an Option - Use a Device (Use a USB, network connection, or Windows recovery DVD) I see the following:
ubuntu
EFI Network
EFI USB Device
EFI DVD/CDROM

Selecting Ubuntu loads perfectly. Yahoo!

Only complaint is the only way I currently know how to access this Uefi is first boot into Windows 8 then select Charm - Change PC Settings - General - Advance - Restart now  ..... A real pain but one I can live with for now.

If any one knows if there is a Fn key I can press at the start to load the UEFI please let me know. F2 loads BIOS settings, F12 loads boot sequence (USB, HDD, DVD, Network) Its not the UEFI full GUI menu. Or perhaps there is a step I can do to fix this issue. 

Loving Ubuntu :)

---

### Post by oldfred on 2014-05-08
Does f12 show Ubuntu entry?
And in UEFI can you not make the ubuntu entry first? Either with secure boot on or off?

New installs are having issue booting the Windows entry from grub menu when secure boot is on.
And booting from Windows is like your comment where it seems to do a restart or warm reboot to boot into anything else.

Post link to new BootInfo report.

---

