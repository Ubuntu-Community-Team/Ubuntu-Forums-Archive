---
title: "Dual-boot: Ubuntu freezes on restart and shut down"
date: 2017-11-18
forum: Installation &amp; Upgrades
---

### Post by pongy on 2017-11-18
I'm having a very strange issue trying to install Ubuntu. I currently have Windows 10 installed on my SSD, and am trying to dual boot Ubuntu 17.04. I downloaded the iso from the Ubuntu website and used 7-zip to extract the files to my flash drive. Then, I booted using the flash drive and ran the Ubuntu installer. I created a 40GB partition on my SSD and formatted it in the installer to use the ext4 journaling file system. The installation completed smoothly, until it says to reboot the computer for the installation to take effect. When I click on "Restart", my computer completely freezes and I am forced to shut down my computer by holding the power button. The installation does not appear to complete because when I restart my computer without the flash drive, my BIOS cannot find GRUB anywhere on the SSD.

This issue is not related to the installer itself. Even when I boot off the flash drive using "try Ubuntu without installing" on the GRUB menu and then try to restart/shut down (without running the installer), my computer freezes completely. I have tried many different things, to no avail. I tried using a different (brand new) flash drive, installing Ubuntu on my hard drive instead of my SSD, changing the BIOS settings, changing GRUB's boot options, running a boot-repair, changing the usb port for my flash drive, using a different Ubuntu version (16.04 LTS), etc. Nothing has worked. I currently have secure boot disabled and am using UEFI boot mode.

I have tried changing the GRUB boot options. I deleted "quiet splash" and replaced it with "nouveau.modeset=0". When I try to restart using these boot options, my computer no longer freezes, and I can see command line output right before the computer shuts off. I am getting these 2 errors every time:
[FAILED]: Failed unmounting /cdrom.mount
[FAILED]: Failed unmounting /rofs
I have tried searching for people with these errors as well as people with the same reboot/shut down issues as me, but none of the solutions I found worked. Hopefully someone can help me out here; I am at a loss at this point...

---

