---
title: "Ubuntu 13.10 Not seeing windows Install"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by rigel4 on 2014-02-11
I am perplexed with this issue!
Not a new Ubuntu user and so I can't understand why this is happening to me.


The problem.

Running windows 8.1 and when Installing Ubuntu the Installer doesn't see the Windows partition.

Things I have tried myself!

Was running Windows 7 and using Linux Live usb key ..same result.. Doesn't see windows and if i choose
other in partition tools .. Ubuntu Installer see's  my disk as unallocated .

I then Installed windows 8.1 .. I was going to anyway.. so clean install and then tried Linux Live Usb .. same result.

Downloaded a fresh copy of Ubuntu 13.10 ..burned to dvd and tried again .. same result.. Ubuntu doesn't see
any other operating system on my disk. 

Tried gparted from live.. Gparted only sees unallocated space..

Need some help guys.. missing my 'buntu

---

### Post by rigel4 on 2014-02-12
I have discovered the problem.. when I last updated my BIOS i have inadvertently 
switched on secure boot and EFI.. not sure what to do about it. Don't really
want to re-install windows again.. using legacy OS and switch off secure boot.

Anyone got any ideas

---

### Post by frank18 on 2014-02-12
> **rigel4 said:**
> I have discovered the problem.. when I last updated my BIOS i have inadvertently 
switched on secure boot and EFI.. not sure what to do about it. Don't really
want to re-install windows again.. using legacy OS and switch off secure boot.

Anyone got any ideas

Do you have The Linux installed with Virtualbox? if don't you should, there are much info how to install linux in virtual box along side win.

---

### Post by mastablasta on 2014-02-13
you can try to install Ubuntu in EFI mode: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.

furthermore even with secure boot on it should still be able to instal:
> [h=1]SecureBoot[/h]"[Secure Boot]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")" is a new UEFI feature that appeared in 2012, with Windows8 preinstalled computers. All current Ubuntu 64bit ([not 32bit]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")) versions now support this feature, but as PCs implementing support for it have only become widespread at the end of 2012 it is not yet widely tested, so it's possible that you may encounter problems booting Ubuntu under Secure Boot. If you do, please file a bug report against the [shim]("https://bugs.launchpad.net/ubuntu/+source/shim/") package in Ubuntu, preferably using the command ubuntu-bug shim once you've installed with Secure Boot disabled. 


are you maybe using 32bit version of the OS?

---

### Post by rigel4 on 2014-02-14
Thanks for your reply.. I will try and the link you have kindly provided to install with EFI mode.

I'm still without Ubuntu and really miss using it.

I'll come back when i have had time to try the EFI route.

Thank you.

---

### Post by Gordonbp531 on 2014-02-16
There's a bug in the 13.10 installer.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564)

Install 13.04 (which DOES see the Windows 8 install) and then update to 13.10.
13.04 installs with UEFI quite happily.

---

