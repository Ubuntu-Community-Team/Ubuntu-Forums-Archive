---
title: "Clean install of 19.10 via USB to Acer Aspire A515"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by bmcraec on 2020-04-15
My friend wanted to get her laptop working again, as the Windows 10 installation was completely borked, and unrepairable without a complete flush and rebuild, but getting a UEFI Windows .iso USB installer built that would load proved so painful, we decided it would be better to get the laptop onto Ubuntu. She does all her stuff with browsers, so there’s no need for Microsoft tools at all.

After much faffing about getting the UEFI Grub file identified on the installer stick, the installs crashed or stalled out for long periods at many places early in the installation. Eventually I fathomed that it MIGHT be either a SSD or USB hardware issue, or an overheating issue, so after building three installers and failing multiple times with each, I opened the case, turned it on it’s side, and got a fan blowing on the naked motherboard while the install ran one more time to the user account creation and install, where it is still churning, over three hours later. 

My Question: How long have people found that 19.10 takes to install? I see the spinning ball with it’s green speed indicators churning and the screen is staying solidly on. There is no progress indicator, so just wondering if there’s a possibility the install has hung, with the progress animation still running. Anybody experience anything like this? Do I let it run all night, or kick it and do the whole damn thing all over again?

---

### Post by oldfred on 2020-04-15
I have installed in under 10 minutes, using toram so entire ISO is in RAM and install is to fast SSD.
Even install to USB3 SSD was almost as fast as that surprised me. Installs to USB3 flash drive are 40 minutes to an hour.
And tried full install to 2006 laptop with 1.5GB and after  two days it was still spinning. Installed server in less than half an hour and updated to lightweight gui.

Most Acer need UEFI update and if SSD, SSD firmware update.

If you have nVidia, you need modeset in grub menu on linux line. New versions will now give option to install nVidia proprietary driver, but if not installed, then you need nomodeset on first boot and then install nVidia driver from inside your install.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You also need to set "trust" after install with all Acer.
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 

Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by eantolinos on 2020-04-21
I did install in an Acer aspireone and it took 45min aprox from usb 1.0

---

