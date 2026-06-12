---
title: "GRUB Minimal BASH after 18.04 installation"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by paranoidcoder on 2018-07-10
First of all, I have installed 18.04 on this rig several times with no issue, so after troubleshooting this for hours I am quite perplexed. Since yesterday, every time I try and install Ubuntu 18.04 I get stuck at the minimal BASH-like command line post installation.

What I have tried:- Tested 2 different flash drives, one of which I have used to install on my system previously
- Restore UEFI/BIOS defaults
- Disable secure boot/fast boot
- Unplug all drives other than destination drive
- Ensure the UEFI Ubuntu install option is booted
- Perform a "Normal install" without downloading updates or extra packages

BootInfo summary from Boot-Repair: [http://paste.ubuntu.com/p/PwWVWnN6FB/](http://paste.ubuntu.com/p/PwWVWnN6FB/)
Log after Boot-Repair failed: [http://paste.ubuntu.com/p/XwWDxf4xt5/](http://paste.ubuntu.com/p/XwWDxf4xt5/)

The only issue I see in the Boot-Repair logs involves sdb1 which is my flash drive, and I'm not sure why that would be causing issues with Boot-Repair.

EDIT
Just had an interesting success with an 18.04 installation. The only thing I did different was unplug my ethernet and I didn't connect to WiFi at all, so my computer had no internet connection.

I just reinstalled with internet access (normal installation, no third party packages or downloading updates) and I got stuck at the BASH-like interface yet again.

So, I tried installing one more time without internet access (normal installation, no third party packages).

So this clearly looks to be an issue with the installer doing something different if it has access to the internet, but I'm not sure what that is. I'm guessing that it attempts to pull down the most recent version of GRUB or something, but I would love to hear if anyone on these forums knows for sure.

I created a Launchpad bug if anyone wants to add their feedback: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042)

---

### Post by powerjas on 2018-07-10
not sure if this is any help but, right after I installed with no network. I did run apt upgrade to get everything updated and this was the last few lines so it is installing and configuring grub. I was able reboot in to the desktop after the upgrade as well, so it only seems to happen during the install process.

/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.15.0-23-generic
Found initrd image: /boot/initrd.img-4.15.0-23-generic
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Adding boot menu entry for EFI firmware configuration

---

