---
title: "USB  boot option"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2016-05-03
Cannot get USB boot option to appear using Dell XPS 11 with Aptio Setup Utility which has Boot Options for UEFI and Legacy.
There are various methods shown but none seem to work. It seems the option has to be entered manually but i cannot get to the file menu.

---

### Post by ajgreeny on 2016-05-03
Does the machine have a one-time keypress to change the boot device?

Most computers have this, often F8, F11, or something else similar to that.  Most machines also show a quick screen message at boot telling you what to use.

---

### Post by angel mike on 2016-05-03
Not as far as I can see. F1 help gives explanation of each item but not much use. F8 sets defaults. F12 gives summary of boot mode with options to reset.
The Boot Option for a USB has to be input manually as far as I have read on other blogs. You set the Name to USB Boot ( though it can be anything) then you tab past the File System List ( which I do not have) Leave the fie name blank and get selection prompt like EFI\Boot\bootx64.efi but this was for another Dell machine so am stuck - think the best way forward is to get something out of Dell. Cannot understand why the option is not listed by default.

---

### Post by pfeiffep on 2016-05-03
[From Dell's site ... ]("http://www.dell.com/support/article/us/en/04/SLN287181/en")

You may also choose **Advanced startup** which will allow  you to start up from a USB drive or DVD drive, change your PCs firmware  settings, or change your Windows startup settings.

---

### Post by angel mike on 2016-05-04
Yes aware of Advanced in Setup Utility after tapping on F2 and trying to setup boot options in Boot section but the help instruction are not much use.

---

### Post by ajgreeny on 2016-05-04
Telling us "the help instructions are not much use." does not really help us to help you.

What exactly happens when you go to Advanced in the setup facility; we may be able to unscramble what it says and help you.

---

### Post by sudodus on 2016-05-04
Maybe the following link to a paragraph about booting from USB can help you. In some computers USB drives are listed among hard disk drives.

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

Otherwise it might work via one of the hotkeys F9, F10 or f12 during boot (or the Escape key if in UEFI mode).

---

### Post by angel mike on 2016-05-04
Sorry about that - thanks for continued help !
Advanced has the following headings with just enabled or disabled options
Intel Speed step
Virtualization
USB Emulation
USB Powershare
usb Wake Support
Intel Smart Connect
In the Boot section the headings are
Boot list Option ( UEFI or Legacy
File Browser Add Boot Option
File Browser Del Boot Option
Secure Boot
Load Legacy Option Rom
Boot option Prorities
Boot Option 1 USB ( i added this)
Boot Option 2 Ubuntu

I have just swapped the Boot Options round and am led into the Shim UEFI Key Management window then I can get into a window MOK Management Window and also into Grub GNU but all this is foreign territory for me ! I have read that you enter the alternative boot option which  I called USB ( but could be anything) - then the next step is to get into the File System List where there is only one option - USB. Leave the file name blank press enter and get a selection prompt something like EFI\Boot|bootx64.efi.  But I cannot get the File System List up !

---

