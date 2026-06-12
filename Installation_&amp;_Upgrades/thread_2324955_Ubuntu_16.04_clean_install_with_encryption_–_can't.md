---
title: "Ubuntu 16.04 clean install with encryption – can't boot via Live DVD or USB"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by Phillip_Spencer on 2016-05-17
I have a Toshiba Satellite L50 laptop (Intel Core i5-4200M & NVIDIA GeForce GT 740M) that is several years old and, until recently, had been running Ubuntu 14.04 (64bit AMD desktop version) without problems.  Last week, I did a clean install of Ubuntu 16.04 (AMD64 desktop version). The only major thing I did differently is that rather than just encrypt my Home directory I chose to use Encrypted LVM to encrypt the hard drive. 

I can boot into 16.04 on the hard drive but when I try to boot from the installation Ubuntu DVD or using bootable USBs (Ubuntu 14.04 and another Linux system that booted without problems before) I cannot and just go straight to the screen to “unlock disk sda3-crypt”. I enter the password and go into the normal hard drive installation.

Gparted shows the following partitions:

/dev/sda1  EFI Systems partition        FAT32        Mount point /boot/efi Size    512.00 MiB    Used    8.45 MiB    Unused    503.55 MiB    Flags: boot; esp

/dev/sda2                      EXT2        Mount point /boot  Size    488.00 MiB    Used    128.84MiB    Unused    359.16 MiB

/dev/sda3                    crypt-luks Size    930.54 GiB    Used    -    Unused    -

I have checked the Start-up settings and these include:
Boot order: 1) ODD 2) USB 3) HDD 4) LAN (so the order looks right)
Boot speed = Normal
Boot mode = UEFI Boot
Secure Boot = Disabled
All the above appear to be the same values that worked properly under the previous 14.04 version.

My understanding is that having encrypted LVM on sda3 should not make any difference to booting as this is done through a different partition. (Note: looking through the Ubuntu Forum for solutions to similar problems, I have seen advice forum moderator “Oldfred” to avoid encrypting with LVM and will not do this in future. Unfortunately, to do this on this laptop I need to be able to boot via my Ubuntu DVD to reinstall without LVM.)

When booting previously to 14.04 I would see a Grub menu before going to the Ubuntu log-in screen. With the new 16.04 install I do not see any Grub menu and go from the Toshiba power on screen via a blank purple screen to the sda3 decrypt screen so I wonder a) if Grub is where the problem lies and b) if I need to run Boot Repair. However, I do not know enough about the boot process to know if this is correct so would welcome some feedback before fiddling and causing more problems.

While not an urgent problem as I can use the laptop for the time being, it is inconvenient being unable to use either DVD or USB to boot other OSs from time to time. If unresolved, it will be a major issue installing a different OS in the future so advice on how to sort this out would be much appreciated.

---

### Post by sudodus on 2016-05-18
Welcome to the Ubuntu Forums :-)

You are right, the computer should boot from an external drive independently of what is installed into the internal drive. But the settings of your UEFI system make a difference, and the external media must be bootable in the selected mode, UEFI or {CSM alias BIOS}.

-o-

You can make your computer show the grub menu again (if you wish). But that does does make the computer boot from an external drive directly. You can add a menuentry for the grub bootloader to chainload from the external drive.

See the following links.

Show the grub menu: [Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

Use GRUB_HIDDEN_TIMEOUT= 

Chainloading: [Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

-o-

***Hotkey to select which drive to boot from***

You should also be able to find a hotkey (or hot key combination) via the internet. Press or tap that hotkey during boot. It is the F12 key in [my Toshiba](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/) with Intel i5, and I must be very quick to press it (at once a boot), otherwise the internal drive will be be selected for boot.

---

### Post by Phillip_Spencer on 2016-05-18
Thank you for the reply, Sudodus.

> **sudodus said:**
> 

You are right, the computer should boot from an external drive independently of what is installed into the internal drive. But the settings of your UEFI system make a difference, and the external media must be bootable in the selected mode, UEFI or {CSM alias BIOS}.
I am slightly puzzled on this as the media (DVD and a another Linux system on a USB drive) had previously worked on this laptop with (I thought) the same UEFI settings.
(I would not expect an Ubuntu install to change the UEFI settings and the Ubuntu 16.04 DVD installation disk I burnt from an ISO file, I had assumed was set up to work with UEFI anyway.)

> **sudodus said:**
> 
You can make your computer show the grub menu again (if you wish). But that does does make the computer boot from an external drive directly. You can add a menuentry for the grub bootloader to chainload from the external drive.
OK, from this I understand Grub is not the cause of my problem.

> **sudodus said:**
> 
***Hotkey to select which drive to boot from***

You should also be able to find a hotkey (or hot key combination) via the internet. Press or tap that hotkey during boot. It is the F12 key in [my Toshiba]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/") with Intel i5, and I must be very quick to press it (at once a boot), otherwise the internal drive will be be selected for boot.
I appreciate this tip. I will try it out tomorrow, when I have had time to back up my data beforehand and am less tired and so less liable to make mistakes!

Thanks again for taking the time to give this advice.
Cheers
Phillip

---

### Post by Phillip_Spencer on 2016-05-19
Just a brief note to update that the suggestion below to use the F12 hotkey was successful with booting both a Ubuntu 16.04 Live DVD and a Linux flavour on a USB flash drive.
> **sudodus said:**
> 

***Hotkey to select which drive to boot from***

You should also be able to find a hotkey (or hot key combination) via the internet. Press or tap that hotkey during boot. It is the F12 key in [my Toshiba]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/") with Intel i5, and I must be very quick to press it (at once a boot), otherwise the internal drive will be be selected for boot.

 So simple when you know how! I had never needed this before as just booting up with either a bootable DVD or USB drive inserted worked automatically on my previous install.

I can now close this - and say thanks again for the advice.
Cheers
Phillip

---

### Post by sudodus on 2016-05-19
I'm glad I could help, and thanks for marking this thread as SOLVED :-)

---

