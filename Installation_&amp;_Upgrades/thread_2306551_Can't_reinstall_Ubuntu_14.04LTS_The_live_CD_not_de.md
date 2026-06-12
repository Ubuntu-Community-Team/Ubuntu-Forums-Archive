---
title: "Can't reinstall Ubuntu 14.04LTS: The live CD not detected"
date: 2015-12-16
forum: Installation &amp; Upgrades
---

### Post by RICuser on 2015-12-16
Hi,

For multiple reasons I want to re-install Ubuntu 14.04 LTS in my laptop. Unfortunately the live CD (the same CD that was used to install this OS) is not detected while restarting. it boots in the same way as without the CD. I can see the contents of the CD in the explorer, but it does not bring me to the installation screen where the option to "try ubuntu without installing", and "install ubuntu" options are seen. I have also tried to use a 12.04 CD which gave the same result.

Wondering if this is a common problem.

Any help is appreciated. Thanks

RICuser

---

### Post by Dreamer Fithp Apprentice on 2015-12-16
Possibly you have the boot order set in bios settings (or whatever they call the bios in more modernistic setups) to look at the hard drive first?

Usually during boot there is a brief message that says something like "press some_specified_key to enter bios setup". Often it is either Esc, Del, or a some function key (F1, F2, etc.). Anyway, whatever it is, do it. Poke around in the utility that comes up and find "boot order" or something like that. Set it to look at the CD first. Find and option for "save and reboot".  Careful not to select plain reboot without saving changes. Do it.

If that doesn't do it, maybe the drive is flaky. You could try booting from a usb thumb drive.

---

### Post by sudodus on 2015-12-16
It happens that CD/DVD drives stop working. Maybe it is only dirty. But the problem might be that you have changed some setting in the UEFI/BIOS. Maybe you can change the boot order and make it boot from CD/DVD again.

If the computer is less than 12 years old, it should be possible to boot from a USB drive, typically a USB pendrive. See this link

[Installation From USB Stick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

