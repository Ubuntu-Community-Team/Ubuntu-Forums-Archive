---
title: "Installing GRUB2 from Windows 7"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by stinovlas on 2016-10-02
Hello,

I am having some issues with my friends Samsung Ultrabook. The preinstalled OS was WIN8, but it was becoming slow and since she didn't even like it, I decided to make it dual-boot linux/win. The thing is, I cannot, by any way, access BIOS or the boot sequence menu, the computer does not respond to keys pressed during the POST screen, not even when I had USB keyboard plugged in. So I deleted MBR from WIN and this made BIOS to successfully boot from live ubuntu flash drive. I installed Ubuntu 16.04 LTS and it works ever since. I am wondering, though, how to make Windows to install GRUB2? I know I can install windows by a few commands in GRUB2 to boot from image containing WIN7 installation, but the installation process would install its boot loader.

Thank you for any help.

Filip

---

### Post by Mark Phelps on 2016-10-02
Windows can NOT install GRUB to a Linux filesystem partition because Windows is unable to read or write Linux filesystems.

You need to boot from Linux install media and install GRUB that way.

---

### Post by stinovlas on 2016-10-02
> **Mark Phelps said:**
> Windows can NOT install GRUB to a Linux filesystem partition because Windows is unable to read or write Linux filesystems.

You need to boot from Linux install media and install GRUB that way.

... and since I cannot choose device to boot from and the computer automatically boots from hdd once it finds boot manager there, it is impossible for me to do it...

---

### Post by oldfred on 2016-10-02
If Windows 8 was pre-installed then it is a UEFI system. 

And UEFI has a fast boot setting. That assumes there is no hardware or configuration setting changes that UEFI or with older systems BIOS would have find and uses the previous settings already written to hard drive for OS to use. But then the handover from UEFI to operating system is so fast you have no time to get into UEFI to change settings.
There are instructions in Windows to get to UEFI. And grub has a menu item, last on menu list to get into UEFI. IF UEFI you still should be able to press escape (perhaps several times) before grub starts system booting. Unless you changed grub timeout to zero.

Most should be able to get into UEFI from a key with a cold boot. Then system does recheck for changes. But if laptop you also need to remove battery. After power down also hold power switch for 10 sec or so to totally drain all power. But some have had to remove coin battery on motherboard, or jumper pins on motherboard. A few laptops have a pin hole reset on bottom for same reset.

---

