---
title: "Dual boot install Which way is correct"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2014-05-02
Hello all,
I want to install Ubuntu alongside Windows 8.1 on my new Toshiba laptop. Been reading all about  doing it the last two weeks and getting confused. What I've done so far is download Ubuntu 14.04 64 Bit LTS. MD5sum ckecked out so using UNetbootin I put it on a 8 GB USB stick. When I start the machine, I get the GRUB menu,

                GNU GRUB version 2.02~beta2-9
*Try Ubuntu without installing
 Install Ubuntu
 OEM install (for manufacturers)
 Check disc for defects

but no matter which option I pick, the screen goes black and nothing happens. I tried nomodeset and some acpi changes but nothing works. I changed the BIOS Secure Boot from Enable to Disable and still the same. I then changed the BIOS from UEFI to CSM Boot and it booted, but when I reboot without the USB, I have to change the BIOS back to UEFI for Windows. According to this:

[http://askubuntu.com/questions/272728/black-screen-after-grub-cant-install-uefi](http://askubuntu.com/questions/272728/black-screen-after-grub-cant-install-uefi)

I have to install in legacy mode, (CSM Boot), and use a boot repair disc to correct it. But, according to this:

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

I can install it in UEFI. Which one is correct? Fast boot is disabled in windows. Also, some people say I have to use Windows to make a partiton for Ubuntu and reboot Windows a few times to check the partition. Please note that I have made a Boot Repair CD in case I need it and I have two sets of Windows backed up to DVD's in case my experiment goes haywire.:p

Laptop Details:
Toshiba Satellite C855D-S5201
CPU AMD E-1 1200 APU
Radeon HD Graphics X2
UEFI
4 GB Ram
600 GB HDD 


Many thanks all
magpie

---

### Post by oldfred on 2014-05-02
I wish whoever said to use Windows to create partitions would not have said that. It is so wrong.
Windows cannot create Linux partitions. Windows often converts to dynamic partition which does not work with Linux at all and does not even work with some Windows repair tools.
Use Windows only to shrink the NTFS partition and reboot immediately to let it run chkdsk and make repairs to recognize its new size.
The use installer or gparted to create Linux partitions. Minimum or default install is / (root) and swap. If dual booting often good to have a shared NTFS partition but you still need fast boot or always on hibernation off in Windows. 

Black screen is usually video issue.
What video card/chip do you have.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Backup efi partition and Windows partition before Install of Ubuntu.

Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Some of these are the older 13.10 and 14.04 has fixed a lot of those issues.
      
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by magpie03 on 2014-05-02
Thanks oldfred,
The video is AMD/ATI Radeon HD 7310. Do I have to resize the partition manually in Windows first? Here are the current partitions.

Thanks again
magpie

---

### Post by oldfred on 2014-05-02
Much better to use Windows to shrink its own partition and reboot for it to run its repairs. Make sure fastboot is off and other settings, Windows likes to reset things the way it wants.

The you can install into the unallocated or manually partition.

You may need nomodeset or other boot parameters. Not familiar with AMD as I have nVidia.

---

