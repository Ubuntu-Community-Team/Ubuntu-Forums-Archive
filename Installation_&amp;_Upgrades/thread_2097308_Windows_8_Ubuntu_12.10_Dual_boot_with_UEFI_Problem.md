---
title: "Windows 8 Ubuntu 12.10 Dual boot with UEFI Problems"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by KWPDX80 on 2012-12-22
I am newbie to Ubuntu but have an average knowledge of PC's and figured I'd be able to start in on it without many problems.

The trouble I'm running into seems to  have to do with UEFI boot mode.  With boot mode set to Legacy I am able to boot from USB or CD and install Ubuntu 12.10 64bit but I can no longer access windows.  With UEFI on I get the boot screen and I get the options to try, install, OEM install or check disc.  But no matter what option I choose the screen goes blank and nothing happens.  I can press e or c for edit or command line and I have tried nomodeset and xforcevesa as suggested in other posts.

My hardware is a new MSI GE60 Laptop with a Crucial SSD and Nvidia GTX660 graphics.

Please let me know if there is any other information that is needed, you know the solution or if there is already a thread with a solution that I have missed.

---

### Post by oldfred on 2012-12-23
Welcome to the forums.

Did you install the 64 bit version?

You do have to have both Windows & Ubuntu in UEFI mode to work together. But Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc(for BIOS) and installing grub-efi (for UEFI). Ubuntu is the same except for a few minor settings that are updated as part of the change to grub.

You can just install this into your live DVD/flash install media. But boot in UEFI mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by KWPDX80 on 2012-12-23
Yes, I was able to install the 64 bit version in Legacy boot mode.  I have tried to use Boot Repair from a Ubuntu Secure-Remix USB created with LinuxLive but I am only able to access it in Legacy boot not UEFI.  When I try to run it with UEFI on (Secure boot on or off) I get the normal screen of options but no matter what I choose the screen goes blank and nothing happens.  

Is there a way to do the boot repair from Legacy mode? Or am I just missing something for starting in UEFI mode?  I can do a boot info report from live USB in Legacy mode if that helps.

I'm sure my problems are something simple but I just don't see what.

---

### Post by oldfred on 2012-12-23
It sounds like a video issue if screen goes blank. I have that issue with my BIOS system and nVidia and have to use nomodeset.
But I am surprised you do not get issue with legacy/BIOS but do with efi boot. That may be just the grub video not Ubuntu's??

Boot-Repair has an option on setting grub's gfxmode to a default, I might try that.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

    
       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

    
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by KWPDX80 on 2012-12-23
Here is the URL from boot repair in running in Legacy mode off a live USB.

[http://paste.ubuntu.com/1460397/](http://paste.ubuntu.com/1460397/)

Hopefully this is helpful.

If I try the recommended repair it tells me to paste this into the terminal:

sudo chroot "/mnt/boot-sav/sdb5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sdb5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sdb5" apt-get purge -y --force-yes grub*-common shim* linux-signed*

I am trying these suggestions now (but again I am working off the Live USB in Legacy mode): 
Boot-Repair has an option on setting grub's gfxmode to a default, I might try that.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

My results:

buntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb5" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb5" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb5" apt-get purge -y --force-yes grub*-common shim* linux-signed*

GRUB is still present. Please try again.

---

### Post by oldfred on 2012-12-23
I think because you are booting in legacy mode you have to force the efi. I have not seen that before. 
Most boot in UEFI mode and then it will convert.

You have/had the BIOS version installed as you have bios_grub partition and grub2's boot loader in the PBR -  partition boot sector.

---

