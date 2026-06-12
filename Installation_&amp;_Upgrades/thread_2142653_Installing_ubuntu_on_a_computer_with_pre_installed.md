---
title: "Installing ubuntu on a computer with pre installed windows 8"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by hey1234 on 2013-05-06
I successfully completed installation of ubuntu 12.04 on a computer with preinstalled windows 8 but when i restarted after installation it didn't show the option for selecting the OS but instead loads windows 8 without giving an option for selecting  OS.Now I  am not able to boot ubuntu.

---

### Post by Hodevah on 2013-05-06
Did you give Ubuntu the option of replacing WIndow's MBR with Grub?

The other route you can follow is to use Boot Repair. Use the Boot Repair option on Ubuntu Secure Remix to install Grub2. 
[http://sourceforge.net/p/linux-secure/wiki/Home/](http://sourceforge.net/p/linux-secure/wiki/Home/)

or download from here:

[http://linux.softpedia.com/progDownload/Ubuntu-Secured-Remix-Download-79225.html](http://linux.softpedia.com/progDownload/Ubuntu-Secured-Remix-Download-79225.html)

When you burn to CD, run it. Make sure you are connected to Internet. Then find Boot Repair. Select Recommend Repair> follow through the prompts. Done.

---

### Post by oldfred on 2013-05-06
Boot-Repair is a good suggestion. It also works on UEFI systems that do not boot with MBR. You can temporarily install to your existing Ubuntu install flash drive.

Did you install Ubuntu in UEFI mode or BIOS mode? Does your Windows system boot with Secure boot off? Some have to have secure boot on and some will only boot the Windows efi file, but Boot-Repair & grub have a work around for those systems.

---

