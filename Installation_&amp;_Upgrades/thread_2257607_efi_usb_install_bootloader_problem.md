---
title: "efi usb install bootloader problem"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by ip3t on 2014-12-21
hi,
i've tried to install Ubuntu 14.10 64bit from usb on an Asus VC60 with this BIOS settings:
[LIST]
[*]Fast Boot = Disable
[*]Secure Boot = Disable
[*]Compatibility Support Module = Enable
[LIST]
[*]Boot Devie Control => UEFI and Legacy OpROM
[*]Boot From Storage Device => UEFI drive first
[/LIST]
[/LIST]

I followed this ufficial guide ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
[LIST]
[*]usb is booted in EFI mode (grub select screen)
[*]clear install
[/LIST]

When reboot on screen appear: "Reboot and select proper Boot device or insert Boot Media in selected Boot device and press any key"

If i set the bios CSM to legacy mode only, and the usb is booted in legacy mode, after a fresh install appear a black screen with the cursore blinking...


I think there're problems with Asus vc60 bios settings...

any ideas?
thanks!

---

### Post by ip3t on 2014-12-21
update:
after i fixed a bug ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865)) using the first workaround, at the end of the installation process appears to me an error windows like this:
"The grub-efi-amd64-signed package failed to install into / target " 
    => another minor bug caused by apparently no stabile wifi internet connection | ok if try to install with etheret support

Now the reboot it's ok | no errors at all!

---

