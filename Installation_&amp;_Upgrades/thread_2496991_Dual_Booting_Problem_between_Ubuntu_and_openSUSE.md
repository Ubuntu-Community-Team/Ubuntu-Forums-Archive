---
title: "Dual Booting Problem between Ubuntu and openSUSE"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by Featherfoot on 2024-04-18
I am trying to set up a dual boot situation with Ubuntu and openSUSE (for redundancy.)  I have done this previously but this is the first time I have tried this with UEFI enabled.After many tries I did a clean installation with the EFI partition reformatted. I installed openSUSE first and Ubuntu second. The BIOS shows GRUB entries for both installations. Both grub entries will boot the system that was used to create them. The Ubuntu system, being installed second, had entries for both Ubuntu and openSUSE, but only the Ubuntu system will boot.  The error message was "Bad Shim Signature."The openSUSE forums suggested enrolling the openSUSE signing certificate as a MOK and suggested that I use the command,mokutil --import /mountpoint/etc/uefi/certs/*-shim.crt where mountpoint was the  openSUSE root partition; i.e.; /etc/opensuse on my system.  They said I would see a "blue screen" and I could then enroll the key on the next boot.I did this  This time I got the message; “Bad Shim signature”/ “You need to load the kernel first.” The next boot did not bring up any screens allowing me to "Enroll the key."At that point, they refereed me to the Ubuntu forums for your wisdom. They talked about mm64.efi and MokManager but gave no other direction. Can you tell me how to proceed or point me in the right direction?

---

### Post by yancek on 2024-04-19
Do you have Secure boot enabled in the BIOS?  Was it on when you installed Opensuse?

>  where mountpoint was the  openSUSE root partition; i.e.; /etc/opensuse on  

That seems unusual as partitions generally are available on Ubuntu under /media/username (replace username with your actual username).  Use lsblk or blkid to get the mount point for your various partitions.  These commands will not identify as Opensuse so you will need to know which partition is Opensuse to get the actual mount point.

If you still have problems, you could get more detailed information by using the 2nd option with boot repair as described at the site below.  Do not do repairs but rather select the option to Create Bootinfo Summary and post the link you get after running boot repair here at the forums to get help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
  
If you are able to boot by selecting either OS from the EFI boot menu then Opensuse is booting with its Grub and Ubuntu with its Grub.

Do you intend/want to boot both from Ubuntu or from Opensuse?

---

### Post by Featherfoot on 2024-04-19
Here is the paste URL:[https://paste.ubuntu.com/p/8pkqcby35K/](https://paste.ubuntu.com/p/8pkqcby35K/)

The specific problem is booting openSUSE from a Ubuntu-built GRUB entry. The error messages are ""Bad Shim Signature" and the next line is "You need to load the kernel first."

---

### Post by oldfred on 2024-04-19
It looks like Opensuse is installed in old BIOS boot mode to very old MBR(msdos) partitioned drive sda.
You have a grub (Opensuse?) in MBR of sda.

But you also have Opensuse entry in UEFI on sdb drive, so either reinstalled or repaired in UEFI mode, but using ESP - efi system partition on sdb.
UEFI & BIOS boot modes are not compatible. UEFI/BIOS writes drive info onto hard drive for operating system differently. So once you start to boot, you cannot switch. Or grub can only boot anther install in same boot mode. You can directly boot an install by directly booting it, but it will be in the original boot mode. I have booted my UEFI install on external drive with a BIOS boot on a very old laptop. but then it is running in BIOS mode.

Do you need or want UEFI Secure Boot on?
You have to have installed with it on, so all of grub & kernels are signed.
If you installed Ubuntu with Secure boot on, it cannot boot an Opensuse install that was not installed in Secure boot mode. Probably easier to totally reinstall in UEFI mode to gpt drive. Note that conversion from MBR to gpt will totally erase drive, so have good backups of any data partitions you want to keep.

---

### Post by MAFoElffen on 2024-04-19
This goes for all Liux Distro's...

Well, there are a few things... If OpenSUSE was installed as BIOS Legacy, and Ubuntu Installed as UEFI, then if you booted from an OpenSuse LiveUsb (similar Distro), then mount and chroot into the affected Linux System, then you could install/reinstall the needed flavor/type of bootloader for it and have it configure on our system.

That is the why, In 2012, I saw the need for the Ama-Gi Project, which was to generically mount installed Linux systems, so they could be repaired. There is still the need for that, but I can't do that work alone. I now just share how to do that, so people can repair their systems. A lot of the code is already written, but needs to be updated, for changes.

---

