---
title: "How do let UEFI access Grub menu?"
date: 2016-12-06
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2016-12-06
I have a Dell Inspiron laptop has come with Ubuntu 14.4 installed.  I would like to install another Linux or Ubuntu variant along side it.  I have disabled "secure boot" and "fast boot" but the machine still boots into 14.4 without question.  Can I make the grub menu appear?  I have read [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but I am still unclear about what I need to do - it is mostly concerned with dual windows/linux systems.

I can switch off UEFI booting and successfully boot from a USB disc.  I have not had any success booting from the internal disc in this way.  Can this be done - and if so, what boot loader should I use (GPT partitions), what flags do I need on the partitions and will doing this disable the UEFI boot completely?  So far the UEFI has remained untouched despite putting extlinux into the MBR (phew!).

---

### Post by yancek on 2016-12-06
If you current Ubuntu is installed using UEFI, then you would need to install the second Linux system UEFI or you will have problems.  That is explained at the link you posted and a command to determine whether your system is UEFI is also give.

I'm not sure why you want the Grub menu to appear as it seems you want to boot from a usb drive to install another Linux system, is that correct?  If you are able to set the usb drive to first boot priority in the BIOS, then do that and boot the installation medium of the new OS to install.

If your Ubuntu is installed UEFI, then you don't want to turn it off to boot off the hard drive.
The standard bootloader for years on most Linux systems is Grub which is what Ubuntu uses.
You don't need any flags set for boot on a Linux system.
If you are using UEFI, you should not have any boot code in the MBR.

I'm not clear on where you are, if you are still trying to boot to install or you have a second install?

---

### Post by Colin@oxford on 2016-12-06
I have use the USB drive simply to test that the version will work on this machine.  I want to install it on the internal drive.

I would like to be able to select the OS I use at boot time.  Grub allowed me to do this.  Can I do something similar with UEFI?
If it means switching from UEFI to legacy boot in the BIOS, I am reasonably happy with this, but I cannot yet find a way of getting the Grub to work when I do this.
I have installed the second system, but have not yet managed to boot from the internal drive.

---

### Post by ubfan1 on 2016-12-06
Try running sudo update-grub   to update the grub.cfg file.  That should pick up the second install.  With two Ubuntu installations, there is possible confusion which grub files you are using, usually the last one installed, but sounds like you are still just running off the first.  You are confused about what UEFI is -- it is not a bootloader like grub, it is the firmware which allows running multiple bootloaders off a FAT filesystem, with some non-volitile memory to remember which one you want to run first.

---

### Post by oldfred on 2016-12-06
If you installed the second system in BIOS mode, the two installs will not see each other for booting. UEFI and BIOS are not compatible, they write the system configuration data differently onto hard drive for operating system to use.
You can only dual boot from grub if all systems are installed in same boot mode.

Lots of info on UEFI in link in my signature.

---

### Post by Colin@oxford on 2016-12-07
I am getting more confused!  Let me say what I think I understand and someone can correct me.

In the old BIS boot, the firmware reads the first few bytes of the disc or partition (the MBR) which for linux will contain GRUB (stage 1) [ or on older systems LILO].  This then reads in (from a fixed point on the disc) GRUB (stage 2) which displays a menu and then boots vmlinux and initrd.

For UEFI, the firmware knows how to read a vfat partition and finds an EFI file (which one?).  This then boots the OS.  Or does it go to GRUB (stage 2)?  If the latter, it implies that all OSs can boot through GRUB, which seems to imply that they don't need a special mode to boot.  That contradicts the assertion that only some OSs can boot with UEFI.  If the EFI file boots the OS directly, then I can't see how GRUB is involved at all.

yancek said:
> 
If you are using UEFI, you should not have any boot code in the MBR.

Is that "do not need" because it is not read or "must not have" since it is used for some other purpose?  If the former, then I should be able to put a BIOS boot loader into the MBR and still boot from UEFI if I set the machine to that.  This appears to be the case because I have some code in the MBR (possibly only of a partition, though).

Please correct me where I am wrong.

---

### Post by yancek on 2016-12-07
Your assessment of the boot process is correct although the terminology (file names, stage1, stage2) are specific to Grub Legacy rather than Grub2.  Ubuntu has been using Grub2 for seven years.  Different names for similar files on Grub2.

Only newer machines (?last 3 years?) are capable of booting using UEFI and that is hardware/systemboard related.  Older machines do not have that capacity.  The Ubuntu EFI file is a Grub file.  Grub code in the MBR on an EFI system will not be read as it should go directly to the file on the EFI partition.  As to whether you can change the setting in the BIOS on boot to Legacy or EFI and boot that way, I don't know.  You'll need to wait for someone more expert in EFI to respond.

---

### Post by oldfred on 2016-12-07
In the standard UEFI configuration, the parts of grub2 that in BIOS mode are in MBR and the sectors after the MBR (core.img) are in the ESP - efi system partition. 
Either way grub is used to boot, but grub-pc is the BIOS version that uses MBR and core.img.
The UEFI version is grub-efi-amd64. There are other UEFI versions for 32 bit and other types of systems.
I believe you are correct that UEFI can directly boot a system, but then you have to install kernels and a lot of /boot into the ESP and configure system totally differently. Have not done it. Only seen one or two places that even discuss that as an alternative. 

UEFI knows the ESP by seeing a very long GUID code. Parted & gparted use boot flag to assign the GUID code. The gdisk program uses ef00 as code to assign the GUID code.

Use of boot flag with gpt then is totally different than use of boot flag in BIOS/MBR based systems, where boot flag means bootable partition usually used by Windows & syslinux boot loaders, but not grub.

EFI started with Intel in early 2000s. Apple uses EFI or UEFI 1.x but included some features now of UEFI 2 which was version in use when Windows required PC vendors to use. UEFI with Secure Boot was in UEFI 2.x. It changed from Intel's EFI to an organization and UEFI.

 Windows 8 release date: October 26, 2012. Some Windows 7 systems were UEFI just prior to that date, but did not include UEFI Secure Boot as Windows 7 does not support UEFI Secure boot.



There are links to more details on most of that in the link in my signature.

---

### Post by Colin@oxford on 2016-12-07
Thanks all.  It looks as though I need to find out how to get the GRUB menu to display, rather than just booting straight into the OS.

---

### Post by oldfred on 2016-12-07
If your install only sees one system, grub is not normally shown, it assumes you just want to boot default as that is only choice.

If UEFI and booting in UEFI mode you press escape key (perhaps more than once) just after UEFI screen but before grub menu. If UEFI has fast boot on, you may not have time to press a key.

If BIOS boot you press and hold shift key from BIOS until grub menu appears.

---

### Post by 1clue on 2016-12-07
[LIST=1]
[*]You either boot UEFI or you don't. All operating systems need to be the same.
[*]Normal UEFI boot has no boot loader. You have a kernel or a stub that EFI knows how to boot.
[*]You CAN use grub or other uefi-savvy boot loaders in place of that stub.
[/LIST]

EFI boot process as I remember it:

[LIST=1]
[*]System looks for a partition with type EF00 formatted as fat32.
[*]System mounts that partition **ONLY**.
[*]Looks in efivars to see which directory to boot from. The first hit that is actually bootable gets control.
[LIST=1]
[*]Default is **/EFI/BOOT/BOOTX64.EFI**. If all else fails your system will fall back to this.
[*]BOOTX64.EFI is either a kernel or a boot loader. In my case it's grub.
[*]There can multiple boot options, you'll need to load all these in your bios.
[/LIST]

[*]If you have a boot loader installed as above, then the system will go through that boot loader at this point.
[/LIST]

I have:
[LIST=1]
[*]/dev/sda1 is EF00/fat32 partition, 512mb because I compile a lot of kernels.
[*]/dev/sda1 is also my /boot partition so it contains the grub directory too.
[/LIST]

EFI boot code cares not one bit what else is on the partition. It also cares not one bit where the EFI partition is mounted in your OS.

---

