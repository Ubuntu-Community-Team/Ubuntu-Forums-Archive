---
title: "usb installation in netbook"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by prudra on 2010-11-27
I have a 32-bit Intel Atom Netbook(no optical CD/DVD tray) where I want to install ubuntu-10.10-netbook-i386.iso OS. At present I have installed opensuse-11.3 in it from an installation-usb created on my 32-bit Dell-Vostro-1014 Gnome laptop with debian-lenny OS by the terminal command
#dd if=opensuse-11.3-Gnome-LiveCD-i686.iso of=/dev/sdb bs=4M
When I created installation-usb for ubuntu-10.10-netbook by similar terminal command and used it to
install it on the Netbook, it simply ignored it booted to the hard disk. Where did I made a mistake?
And how shall I succeed?
Thanks for guidance.
P.Rudra.

---

### Post by cybergnome on 2010-11-28
Permissions are handled differently by different Linux distros.  Ubuntu users who wish to use the terminal as root have to preface the command(s) with the "sudo" command.

---

### Post by C.S.Cameron on 2010-11-28
Usb-creator, (from the Live CD), UNnetbootin and Universal, (from pendrivelinux.com), and MultiBootUSB, are all good tools for installing Ubuntu to pendrive.

---

### Post by sikander3786 on 2010-11-28
> **C.S.Cameron said:**
> Usb-creator, (from the Live CD), UNnetbootin and Universal, (from pendrivelinux.com), and MultiBootUSB, are all good tools for installing Ubuntu to pendrive.
And here are the links ;-)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by C.S.Cameron on 2010-11-28
[http://sourceforge.net/projects/multibootusb/](http://sourceforge.net/projects/multibootusb/)

---

