---
title: "Upgraded to 19.10, stuck on purple screen, no way to pass even with cd/usb boot"
date: 2020-03-08
forum: Installation &amp; Upgrades
---

### Post by palavilli11 on 2020-03-08
Hi all,

I have recently upgraded to 19.10 and am now totally stuck. Not only can I not get past the purple screen with flashing dots, I cannot even get into boot mode with any of the 100s of key combinations at start time, nor can I boot with a CD or live-USB. Any hints how I can get my machine back in any way, shape, or form would be much appreciated. I've never had this level of disaster upgrading in my 30 years of Linux. Thanks in advance.

---

### Post by yancek on 2020-03-08
When you upgraded from 19.04, did you have any problems with the upgrade; warning or error messages?  If so, post them.  Are you not able to access the BIOS on the machine so that you can boot from a 'live' usb?  Post hardware (computer) manufacturer name.

---

### Post by palavilli11 on 2020-03-09
No errors during upgrade and everything seemed to go smoothly. There is no way to bypass Ubuntu purple screen it seems and I just cannot get into BIOS with any normal key combinations (tried several). I would happily reinstall if I can get into the bios. 

It is a 5 year old HP Pavilion desktop with AMD processor. I can post more once I get home if needed but I'd say it is a typical machine. Thanks for the help.

---

### Post by CelticWarrior on 2020-03-09
New HP (with UEFI) typically respond to (spamming) ESC right after powering on. Then you should see a menu with, among others options, F9 to select the one time boot menu and F10 to access UEFI settings (you don't actually have BIOS and that distinction matters when installing OSes, Ubuntu or Windows).

---

### Post by palavilli11 on 2020-03-09
I used to be able to get into BIOS (with ESC) up until this upgrade. Had it dualboot Windows earlier before I went pure Linux and then this upgrade now blocks everything it seems with that purple screen with blinking dots.

---

### Post by CelticWarrior on 2020-03-09
No, it doesn't.

Accessing BIOS/UEFI isn't related to installed OSes. It happens before the OS starts to load. New UEFI features such as Fast Boot make it harder but not impossible, it just needs you to be faster, like one finger powering on, another immediately spamming ESC (or whatever key is mentioned in the users' manual). But if you can't do it fast enough, you can disconnect the boot drive and then you will. First thing to do is disable Fast Boot, of course. After that reconnect the drive and try booting from USB, backup and reinstall from scratch, preferably in UEFI mode.

---

### Post by dragonfly41 on 2020-03-09
I changed over to using [rEFInd]("https://www.rodsbooks.com/refind/installing.html") to complement the standard GRUB system in UEFI mode.

$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind

This installs this file system.

/boot/efi/EFI/refind/

Now in that folder you can customise further by tweaking settings refind.conf, for example adding a delay.

[Further references]("https://forums.linuxmint.com/viewtopic.php?t=287353").

---

### Post by palavilli11 on 2020-03-10
I will try disconnectiing the boot-device. Thank you.

---

