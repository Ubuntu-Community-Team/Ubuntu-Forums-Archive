---
title: "Invalid EFI file path"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by daniel-abad-85 on 2013-12-21
Hi,

I was trying to make a dual boot with Windows7 and Ubuntu 12.04, i try to find how to make it works since 1 week, i did all things i find or forums, etc...and test many options. Im totally desperate now...

I have 4 hd:

OCZ 120 SSD 120gb
SAMSUNG 840EVO SSD 120gb
WD Caviar HD 300gb
WD Caviar HD 250gb

I want have installed Windows 7 on OCZ and trying to install Ubuntu on Samsung. The other two hds are just for windows files, donwloads, etc....

Im installing ubuntu from a USB UEFI, after many attemps, i make a clean installation of Windows 7 from UEFI CD.

When i enter ubuntu options i select "something else", i create 3 partitions on Samsung:

4gb swap
100mb efi boot
rest ext4

When im in grub2 and i try to start windows 7, i get the error : invalid EFI file path...

I tried many partitions configurations, checked bios options about DHCI or something similar, tried to make a boot repair but program tells me something is mount, even im in "try ubuntu" option.

At boot options i have Samsung as 1st HD and ubuntu loader as 1st option.

I tried refind boot but doesnt recognize the windows, and now i dont know how to unistall it...

I read a lot of documentation, similar errors and no one works for me.

Now, with both systems as EFI, ubuntu dont launch grub2...

There is the boot repair inform:

[http://paste.ubuntu.com/6611681/](http://paste.ubuntu.com/6611681/)

Can anyone help me or guide me to make this works?

Thanks in advice and sorry if i forgive something, im new here.

---

### Post by oldfred on 2013-12-22
Is your system Secure boot capable? It looks like you installed Ubuntu with the signed kernels & grub. But only secure boot systems can use that.
Windows 7 is not a secure boot system. So to boot it in UEFI mode you must have secure boot off.

Boot-Repair suggested turning secure boot off and rerunning Boot-Repair and that is also my suggestion.
If Boot-Repair offers the "buggy" UEFI fix say no for now. That is only for those UEFI that have internal code to only boot Windows from UEFI menu. If you can boot both ubuntu and Windows entry from UEFI menu then you do not need that fix.

---

