---
title: "Ubuntu 18.04 and Windows 10...Need help!!!"
date: 2018-10-12
forum: Installation &amp; Upgrades
---

### Post by jnmjr on 2018-10-12
I installed win10 on a second hard drive in my desktop, both drives are samsung ssd's, grub does not see win10, I had no such problem with win7. I tried the usual "sudo update-grub" which always worked with previous versions of windows. I also tried to install grub on sdb (win10) and I get an error message.........Installing for i386-pc platform. grub-install: warning: File system `ntfs' doesn't support embedding. grub-install: error: embedding is not possible, but this is required for cross-disk install. 

Can someone help, I don't know how to solve this, never seen this error message before, my BIOS is set to boot from Ubuntu, it works fine, of course, if I boot from the second HD it boots into Windows.
Thanks in advance for your help.

---

### Post by oldfred on 2018-10-12
You never install grub to the PBR of a NTFS file system as NTFS has essential boot info in it. 
Not sure why you want that for two drive system.
If both installs are UEFI or both BIOS and Windows fast start up is off, grub will boot Windows. And since grub only boots working Windows you can have Windows boot loader in MBR (if BIOS) of Windows drive and directly boot it. Or if UEFI you can always directly boot Windows from UEFI.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

