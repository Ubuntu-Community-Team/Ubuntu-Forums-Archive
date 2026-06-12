---
title: "install on usb hd Samsung T5"
date: 2020-07-19
forum: Installation &amp; Upgrades
---

### Post by mcyber4 on 2020-07-19
Hi
Can I install 20.04 on a external usb samsung t5 ssd hd? Will grub get into my way and mess boot of my hd? Is it fast enough to test 3d apps? Tips for install?
Thanks

---

### Post by oldfred on 2020-07-19
UEFI or BIOS system and current installs?

With external drive, you have to partition in advance & include an ESP on external drive, if you do not physically disconnect internal drives or in UEFI temporarily change to disabled. Ubuntu's Ubiquity installer in UEFI mode, only installs grub to first drive's ESP. Usually that is the Windows efi partition.

Just installed 20.10 to sdb as test and did not want to modify my Ubuntu boot on sda, so had to use this work around.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I have found SSD on USB3 to be faster than HDD. I have full installs on flash drives & they are really slow and used to think it was at least partially the USB3 port.

It only is read & write where SSD are faster. Once a program is loaded into RAM it does not matter where it came from.  So if you can load entire application & its data into RAM, application will be just as fast. Or make sure you have plenty of RAM for large applications.

---

### Post by dragonfly41 on 2020-07-19
Well I am running Ubuntu 18.04 on an external Crucial 1 TB SSD with Dell as the host (containing Windows 10 for when needed).

The key is to research your available USB ports on your Samsung.  My SSD is on USB 3.0 which is _essential _for speed.

I don't have experience with Samsung (I'm a Dell user) but you can search around for blogs. [Here is one]("https://www.theverge.com/2019/5/13/18518127/portable-ssd-external-thunderbolt-3-usb-c-samsung-x5-t5-specs-test-how-to").

Other tips are to create an EFI partition on your external SSD and make sure that your LiveUSB installs Ubuntu as UEFI.
I use GParted to create /dev/sdb1 (EFI 500 MB , Fat32, mount point /boot/efi, with boot flags set) and /dev/sdb2 as ext4 for Ubuntu (mount point /). 

A debatable point is that I have installed rEFInd in /dev/sdb1 to add to the usual Grub loader.

I try to separate Ubuntu from Windows.

@OldFred was first away from the blocks as I was writing.

---

### Post by oldfred on 2020-07-19
> A debatable point is that I have installed rEFInd in /dev/sdb1 to add to the usual Grub loader.


I do not think it is debable, just an option and some systems that seem to have issues will work with rEFInd.
Many with Mac use rEFInd as Mac started using UEFI before PCs did.

I do have several flash drives with rEFInd for emergency boot. My Asus Z97 system gets confused sometimes as I have multiple drives & flash drives with UEFI entries. And when I plug all of them in and start rebooting into a different system the Asus UEFI seems to lock up system. Then unplugging all drives, then adding one & booting with rEFInd seems to be only way to reset. But then UEFI & grub start to work again.

---

### Post by mcyber4 on 2020-07-21
> **oldfred said:**
> 
Many with Mac use rEFInd as Mac started using UEFI before PCs did.


I don't think so. Uefi was created by MS. On my last hackintosh install some years ago I needed to disable UEFI. Also my, some years old, macbook uses EFI.

So if I do 
[COLOR=#000000][FONT=-apple-system]bootrec/fixmbr
[FONT=Verdana][SIZE=2]Could I still boot Ubuntu from T5?[/SIZE]



[/FONT][/FONT][/COLOR]

---

### Post by oldfred on 2020-07-21
EFI was created by Intel and when Apple converted to Intel based chips they used EFI.
Then Intel released EFI to the UEFI Forum  and Microsoft in 2012 with Windows 8 used UEFI v2.x.
Mac as I understood it were part EFI & part UEFI v2 for years, not sure where they are now.

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Windows will not boot Ubuntu/grub. 
But Windows also will not boot from external drives.
With UEFI you can always boot from UEFI boot menu.

If you let Ubuntu do a default install with grub on the internal drives ESP, and set as default boot in UEFI, then you will get a grub error on booting if external drive not plugged in. 
But still can boot Windows directly from UEFI boot menu.
You should be able to set external drive as first in UEFI boot order & Windows as second. Then if external drive not plugged in, it switches to boot Windows automatically. Or if only booting Ubuntu occassionly, have Windows as default and choose in UEFI boot menu to boot external drive.

Note that both Windows & Ubuntu updates may reinstall boot loaders and reset UEFI boot order, so they are first.
And Windows update often resets fast start up to on, so then grub will not boot Windows nor can you use any NTFS partitions from Linux as hibernation flag is set. You have to turn fast start up off again.

---

### Post by mcyber4 on 2020-07-22
> **dragonfly41 said:**
> 

Other tips are to create an EFI partition on your external SSD and make sure that your LiveUSB installs Ubuntu as UEFI.
I use GParted to create /dev/sdb1 (EFI 500 MB , Fat32, mount point /boot/efi, with boot flags set) and /dev/sdb2 as ext4 for Ubuntu (mount point /). 



Thanks I'll try that when I install Ubuntu in some days. If I wouldn't need 3D accelerated Ubuntu, I would go with virtualbox.

---

### Post by pbear42 on 2020-07-23
> **oldfred said:**
> 
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
There's another workaround, relatively simple, which I've found to be 100% reliable.  Per Tim Richardson in this [askubuntu]("https://askubuntu.com/a/1056079") answer, use GParted to unflag the internal drive's EFI partition, install to USB drive, then restore the internal drive's boot flags.  Also works with the similar problem of install to multiple internal drives.

---

