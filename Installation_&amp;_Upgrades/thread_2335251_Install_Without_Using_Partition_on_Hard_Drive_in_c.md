---
title: "Install Without Using Partition on Hard Drive in computer?"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by roeepalmon on 2016-08-26
Hello, I have a flash drive and I would like to install ubuntu on it without having to make a partition on my hard drive. Is it possible to do so? Even with other Operating Systems?

---

### Post by RobGoss on 2016-08-26
Does this machine already have a operation system on it? If in fact it does you will ether need to choose to install Ubuntu along side what ever other OS you have on this machine or create a partition and install Ubuntu on that partition

If you're wanting to install Ubuntu on a flash drive only you might want to look at this guide [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by roeepalmon on 2016-08-26
Right now I have the Windows 10 OS on the computer.

---

### Post by RobGoss on 2016-08-26
> **roeepalmon said:**
> Right now I have the Windows 10 OS on the computer.


Are you wanting to dual boot your system?

And is this your first time attempting to installing Ubuntu?

---

### Post by roeepalmon on 2016-08-26
I've actually installed ubuntu via dual boot on a different computer. I just want to know if I could install it on a flash drive to save space on my hard drive. (Also to try out other Operating Systems)

---

### Post by RobGoss on 2016-08-26
Yes you can install Ubuntu on a flash drive just take a look at post **#2 **I provided the link with instructions

I have never used this method but from what I have read it works well if done correctly. I would assume you would need a flash drive with enough space to save your data those are pretty cheap these day

---

### Post by oldfred on 2016-08-26
You can do a full install to a larger flash drive from a smaller flash drive. It is just like any install to a second drive.

But if Windows 10 is UEFI and you install in UEFI mode, you must partition in advance including an ESP - efi system partition on the flash drive. Grub will install its boot files into the ESP on the internal drive. You then copy those files or the entire /EFI/ubuntu folder to flash drive's ESP. Then you must also create a new /EFI/Boot and copy shimx64.efi into that folder. Then rename to bootx64.efi.

The reason is that grub only installs to sda.
And external drives including installer, only boot in UEFI mode from the ESP or FAT32 partition and from /EFI/Boot/bootx64.efi. Even Windows installer uses that file name, but obviously a different actual file.

---

### Post by roeepalmon on 2016-08-26
Could you do this with other operating systems using a windows software?

---

### Post by RobGoss on 2016-08-26
> **roeepalmon said:**
> Could you do this with other operating systems using a windows software?

Can you explain exactly what you mean by, [B]other operating systems using Windows

[/B]You can use Windows to create the pen-drives and test out other Linux operation systems if this is what you mean

---

### Post by roeepalmon on 2016-08-26
The other operating system that I want to install on a flash drive is Remix OS (Android x86 based Operating System)

---

### Post by RobGoss on 2016-08-26
From what I see you should be able to install it on your hard drive not a USB drive, unless this Android OS has documentation that states other wise I don't really know much about Android Os's you might want to check their forums for more details on it

---

### Post by sudodus on 2016-08-27
You can install a portable Ubuntu mini system that boots in both UEFI and BIOS mode in a USB pendrive according to the following link

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I agree with RobGoss about Remix OS (Android x86 based Operating System). Look for information at their website (document pages, forum pages ...).

-o-

Remember that you can try most linux distros without installing, and you can run persistent live systems with many of them. See

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

