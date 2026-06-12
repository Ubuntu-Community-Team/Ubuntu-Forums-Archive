---
title: "Installation of Ubuntu will not continue after reset - stuck on GNU GRUB"
date: 2017-11-22
forum: Installation &amp; Upgrades
---

### Post by abi.curlew on 2017-11-22
Hey folks, 

I am new to Ubuntu and excited to get started. However, I hit a snag in the installation process. I have an ASPIRE V that is currently running Windows 10. Before I reformatted the disk, I checked to see if Ubuntu would boot from my thumb drive and it did and worked perfectly. The installation process went normally throughout the entire process until the installation finished and asked if I would give permission for a reset. I did so several times but it would take me back to the GNU Grub and I was only met with these options: 

Try ubuntu without installing
install ubuntu 
OEM install 
Check disc for defects

My computer was totally re-formatted and does not run Windows anymore. But, it also did not install ubuntu. If I press ESC, it takes me to a grub menu that allows me to type in code (a skill I am not blessed with). I've tried to tinker with it and tried re-installing several times to the same effect. I've even gone into F2 and made sure the boot order didn't go straight to my thumb drive. 

Has anyone else experienced this and know a work around? I really need this computer for my research and was surprised about the issue. 

Thank you in advance for your help!! :KS:KS

Abigail.

---

### Post by Bucky Ball on 2017-11-22
Welcome Abigail. That message at the end should say 'remove USB or install disk *then* restart', or words to that effect. Unless something's changed in 

Sounds like you're not removing the install media, the machine is restarting and simply booting to the USB/install DVD because it is still in the machine and the BIOS is still set to boot from it. The options in your post are the options that will only be found on the install media, so you still have that in the machine. It shouldn't be there for the first reboot after install.

At the end of the install, when you get the 'restart' message, you should remove install media, boot the machine to the BIOS and set the machine to boot from the appropriate disk, NOT the install media (be it USB or DVD) which is no longer present (or shouldn't be).

Try the above and let us know how it goes. Incidentally, how do you know Ubuntu is not installed? Have you booted from the install media, 'Try Ubuntu' and opened Gparted to have a look? Suggest you do that if you're not sure. The problem may be as simple as a slightly screwy boot manager.

Also, have you installed Ubuntu using UEFI mode or legacy and which release and flavour of Ubuntu are you using? (Ubuntu 16.04, Xubuntu 17.10 or one of the many others?)

---

