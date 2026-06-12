---
title: "Ubuntu no longer boots after ntfs partition resize"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by ferdez on 2014-09-09
Hi all,

I have a "dual boot" machine (Lenovo S540) with windows 8.1 and ubuntu 14.04 installed side by side.

Because I needed more swap space, I decided to shrink the ntfs partition and use the extra space as linux-swap. I used gparted from the live ubuntu on an usb drive. No other partitions were touched. Just divided the ntfs partition in two, creating a linux-swap.

But, after this, ubuntu no longer boots. I get the grub menu, select the ubuntu option, and the it gets back to the menu with no visible error message.

I can access all my files if I mount the partition with the live usb stick. 

Any suggestions?

TIA

Fernando

P.S.:
I write "dual boot" because I have to use the bios device menu to choose how to boot: windows or ubuntu, since the windows selection on the grub menu never worked. But this is not the issue I need fixing.

---

### Post by yancek on 2014-09-09
Can you boot the Ubuntu DVD/flash drive you used to install and run this command from a terminal to get info:  sudo fdisk -l(Lower Case Letter L in the command) post it here.  Also open a terminal and run:  sudo gparted and post that image so we can see your partition structure.  Shrinking windows partitions is usually best done from windows.

---

### Post by kansasnoob on 2014-09-09
If you deleted the previously existing SWAP partition and both it and the Ubuntu root (or /boot) partition were either (both) primary or (both) logical partitions the device designation for / or for /boot (if one exists) may have changed. You can usually get a clue from looking at the /etc/fstab. Even though those lines are commented out it'll show what the device designations were during install so you can compare to what they are now.

If that's the case just running update-grub in a chroot may do the trick.

---

### Post by kansasnoob on 2014-09-09
Just thought to add - I would not use Boot Repair in this situation. Or, more specifically, this statement worries me:

> I write "dual boot" because I have to use the bios device menu to choose how to boot: windows or ubuntu, since the windows selection on the grub menu never worked. But this is not the issue I need fixing. 

So I would not want to run Boot Repair's recommended repair without first looking at the boot info.

---

### Post by ferdez on 2014-09-10
Well, this is embarassing.

I cannot boot ubuntu if I choose the "ubuntu" option in the firmware device list. 

But I **can** boot ubuntu if the firmware is configures to boot "Legacy" as well as "UEFI", with "Legacy first", and I choose the disk name instead of "ubuntu".

This means there's not really a problem with the partitioning. Only with the boot process.

After reading a bit, I realise my ubuntu installation is MBR/Bios and I need to convert it to EFI. 

Now I have a problem with the installed kernel, which does not support the efivars module, but that's another thread: [Trying to convert install on BIOS/MBR to EFI/GPT: can't load efivars kernel module]("http://ubuntuforums.org/showthread.php?t=2243661")

Thanks for the suggestions, guys.

---

