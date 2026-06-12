---
title: "Really works! Install encrypted ubuntu and then windows 10/11"
date: 2024-05-24
forum: Installation &amp; Upgrades
---

### Post by henk982 on 2024-05-24
Hi guys, 

This is my first post after switching to Ubuntu 6 months ago. Really love it. 
One  of my bit questions was how to install Ubuntu with LUKS2. all the  options (with 24.04) where a unencrypted ubuntu next to windows. No  solution really worked so I tried a lot of things. And what worked was  resizing the LVM/LUKS2 volume with Gparte, make a NTFS partition,  install windows, use boot-repair and done. Looks simple but it was a  puzzle. 

All the steps.

1. Install Ubuntu as the only OS on the drive. Erase disk and install ubuntu option. Follow all steps to install Ubuntu. 
2. Start Ubuntu from USB (try ubuntu). 
3. Open (sometimes install) Gparted. Go to encrypted disk and select open encryption. 
4. Now you can free up the space you want for Windows. 
5. Press apply. A empty partition will appear. 
6. Format this partition as NTFS and press apply again. 
7. Reboot in to windows installation USB and during setup you will see the NTFS drive. Install windows here. 
8.  After windows is installed, the computer will start windows, no option  form Ubuntu. Boot into Ubuntu via the bootmanager (almost always F12 at  boot). Not via the USB.
9. Install boot-reapair and run the repair.  Follow all the steps! It will repair Grub so you can choose Ubuntu or  windows at boot. 

Done!

I also set Bitlocker in windows 11 so I now have both systems encrypted. 

Hope this helps.

---

