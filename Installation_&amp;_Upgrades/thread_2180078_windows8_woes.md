---
title: "windows8 woes"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by night116 on 2013-10-11
I have a new computer with a 120Gb SSD drive which windows8 resides. I then have a 2Tb HDD which is partioned ready for ubuntu13.04 to go on.
but when I boot my DVD with ubuntu on it, the comuter firstly boots up stating loading linux, then I get the little keyboard down the bottom of the screen. but then all goes wrong, the screen then goes to no signal and starts blinking it light on the botton of the monitor like no signal is there. the dvd drive is trying to load as I can hear it, but nothing happens.
I checked to make sure it is booting to the DVD first and also checked (Cmdlet not supported on this platform) came up.
please help to get ubuntu on not bloody windows8. I am using ubuntu13.04 64bit

---

### Post by grahammechanical on 2013-10-11
You do need to read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Now to get a Ubuntu live session working you can try this

1) at the first purple screen with the keyboard icon and the icon of a human press Enter
2) at the next screen press Enter to select English as the default language or select another language and press Enter.
3) at the third screen with Try Ubuntu - Install Ubuntu press F6
4) at the bottom right of the screen there will be a little menu. Select nomodest and press Enter. A tick mark will appear next to nomodeset
5) Press Esc to go back to the Try Ubuntu - Install Ubuntu screen and select Try Ubuntu and press Enter.

See if that gets you to a working live session.

By the way, some information on your hardware would be helpful, especially the graphic adapters. Does this machine have Nvida Optimus technology? Or AMD hybrid graphics? It is useful for us to know these things.

Regards.

---

### Post by oldfred on 2013-10-11
As link on UEFI installs that grahammechanical has posted, if you get purple screen with accessibility icons that is a BIOS boot. If you get a grub menu then you have a UEFI boot. How you boot is how it will install.

Is your Windows 8 installed in UEFI mode or BIOS mode? You need Ubuntu in the same boot mode. 

But if Windows is UEFI you will need hard drive  with gpt partitioning for UEFI boot. If not gpt you may be able to convert, but back up any data first. I suggest an efi partition on every drive even if boot loader goes into existing efi partition on another drive. 

Some links to examples where users installed with two hard drives with UEFI in the link in my signature.

---

### Post by night116 on 2013-10-11
that did the trick, got it installed, had to fix the boot with the boot-repair listed. all good, no more bloody windows.

---

