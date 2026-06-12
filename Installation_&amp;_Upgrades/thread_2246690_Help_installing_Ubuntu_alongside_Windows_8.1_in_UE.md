---
title: "Help installing Ubuntu alongside Windows 8.1 in UEFI file system"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by Zahin06 on 2014-10-02
I am using Windows 8.1 on a UEFI system. when I tried to install Ubuntu 14.04 alongside it using an USB drive, it was installed but I can't boot to Ubuntu. It always boots to Windows. One odd thing I noticed was-during installation, Ubuntu didn't seem to find windows as it normally does and suggests to make a dual booting bootloader. I created custom partitions and installed it.

---

### Post by Dennis N on 2014-10-02
This may be the problem: You need to boot Ubuntu installer in UEFI mode, which causes Ubuntu to be installed in UEFI mode. Otherwise grub in Ubuntu won't detect Windows and create the grub menu entry for it that you expect. Your comment that "Ubuntu didn't seem to find windows as it normally does..." suggests this might be what happened.

---

### Post by ubfan1 on 2014-10-02
There seem to be lots of reasons that the installer doesn't find Windows, but at least you didn't wipe out the Windows partitions.  From the live media, mount the efi partition (usually sda1 or sda2, used sda1 in: ( sudo mount -tvfat /dev/sda1 /mnt/<your favorite mount point>) and see if you got the ubuntu directory/files created in /mnt/<your...>/EFI/ubuntu...
  Can you select the ubuntu bootloader (grubx64.efi or shimx6.efi) from the efi menu (some function key, varies by machine), to select devices and oses to boot?  Some machines list all the choices, others may require you to select the hard disk, then you get a window to select either Windows or ubuntu.
If so, the install was in UEFI mode, and you might just need to reorder the default boot so grub (or shim) boots instead of Windows.  From the Windows side bcedit (or something like that) may be used, or from the live media, download the efibootmgr if necessary, and run the efibootmgr to examing the boot choices, and reorder them if needed.
  Did you turn off the Windows power option for "fast startup"?  That basically skips the whole boot process and reads in a Windows from disk.

---

### Post by Zahin06 on 2014-10-03
> **Dennis N said:**
> This may be the problem: You need to boot Ubuntu installer in UEFI mode, which causes Ubuntu to be installed in UEFI mode. Otherwise grub in Ubuntu won't detect Windows and create the grub menu entry for it that you expect. Your comment that "Ubuntu didn't seem to find windows as it normally does..." suggests this might be what happened.

It worked. Thanks a lot. :)

---

### Post by Dennis N on 2014-10-03
@Zahin06

And thanks for the feedback!

---

