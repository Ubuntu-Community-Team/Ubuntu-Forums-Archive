---
title: "How to prevent grub from being installed"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by longint on 2013-03-16
One thing which drives me crazy abaout Ubuntu is that grub gets installed everytime a new kernel hits the stage. I already tried several of the tips and tricks around but did not manage to get comepletely rid of grub. I do not want any boot loader installed, so how do I do this?

I'm running 13.04 on a MacBookPro booting through refind.

TiA

---

### Post by oldfred on 2013-03-16
I do not know Macs, but assume the grub install is the same. In your case unchoose everything and then the install_devices should change to blank.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by longint on 2013-03-16
??
Sorry for being not precise enough: I do NOT want Grub installed at all!

---

### Post by ManamiVixen on 2013-03-16
Grub is absolutley required. It's what boots the PC. If it's not installed, it wont boot!

There are alternative boot loaders like Burg if that tickles your fancy.

---

### Post by ManamiVixen on 2013-03-16
Anyways, if you are new to Ubuntu, why do you have a development release? You need the current 12.10.

---

### Post by longint on 2013-03-16
Please guys lets come back to topic: How do I prevent grub from being installed? I do not need it, nor any other bootloader (already told you in 1st post).

---

### Post by oldfred on 2013-03-16
Refind is not a boot loader:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
> Like rEFIt, rEFInd is a *boot manager,* meaning that it presents a menu of options to the user when the computer first starts up, as shown below. rEFInd is not a *boot loader,* which is a program that loads an OS kernel and hands off control to it.


But it looks like there may be a way, but I have not tried it:
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)

---

### Post by longint on 2013-03-16
Ok, forget about. If someone is having an alternative to setting grub-pc to hold or installing a dummy package, please let me know.

Thx anyway.

---

### Post by schragge on 2013-03-16
Cannot say for Ubuntu (you'll probably need to use Alternate ISO here), but in Debian if you run debian-installer with priority=low (press **F6** on the first screen to add it as kernel option) it will ask if you want to install grub, and you can skip installing boot loader. Besides, IIRC it's the last step in the installation, so you can simply reboot when asked where to install grub.

IMO, a better option than not installing grub at all is install it into boot partition of your Ubuntu installation, say /dev/sda2 (ignore installer warnings that grub should be installed into MBR of the disk). I did it e.g. to let MBR be controlled by Windows BCD on dual-boot setups.

---

### Post by longint on 2013-03-16
My issue is that grub-pc is set as recommended/dependency for linux-image (beside lilo which I also do not want) resulting in getting it installed again every kernel-upgrade and has to me removed manually. Setting grub-pc to hold eases the situation. If there is any way to block it completely (other than installing a dummy package) I'd be interested to learn about. I agree installing in an unused partition will also ease the situation but I'm not a friend of having packages installed which I do not really use.
 
Having kernels able to be booted directly by BIOS this issue could be considered as something like a bug IMHO.

---

### Post by schragge on 2013-03-16
You don't install grub into an unused partition. You install it into the boot sector of your Ubuntu partition and let it handle Ubuntu kernel upgrades. The boot loader in the MBR (in my case it was Windows) doesn't boot Ubuntu kernel directly. Instead, it chain-loads grub in the Ubuntu partition. This way Ubuntu kernel upgrades are handled smoothly and transparently:  Windows boot loader doesn't need to be updated each time you install a new Linux kernel.

---

