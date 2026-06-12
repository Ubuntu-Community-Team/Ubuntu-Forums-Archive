---
title: "Syslinux problem."
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by arron.faulkner on 2014-10-05
I have tried using:

- LinuxLive USB Creator
- Universal USB Installer

and I keep getting the same problem ( look at image ). Any ideas?:

[IMG]http://i.imgur.com/WghcqkQ.jpg[/IMG]

---

### Post by Vladlenin5000 on 2014-10-05
Hi, welcome.

So you've used the usual software supposedly to create a bootable USB.
What OS version and what machine have you tested with?

---

### Post by arron.faulkner on 2014-10-05
Latest Ubuntu ( 14.04.1 desktop amd64 ).

Machine:

Intel Core 2 Quad @ 2.40Ghz
8GB Ram
Installing onto 12gb of a 2tb hard-drive.
AMD HD 5870

---

### Post by Vladlenin5000 on 2014-10-05
If that message appears right after attempting to boot from the USB then:
- The ISO you used might be corrupt. Checking the *checksum* after downloading is always a good idea. Also downloading via torrent usually avoids this kind of problems (the torrent software should verify it while and after it downloads).

If it doesn't appear right after the boot attempt, ie, if it appears somewhere after some graphical interface is shown, then please tell us exactly the steps you took and what happened.

---

### Post by arron.faulkner on 2014-10-05
MD5 Hash check, showed that the file is not corrupt / damaged.

And it appears immediately after attempting to boot from the USB ( the image shows that ).

---

### Post by Vladlenin5000 on 2014-10-05
Let's see if there are similar reports already... Please post hte make/model.

---

### Post by arron.faulkner on 2014-10-05
make/model of what?

---

### Post by Vladlenin5000 on 2014-10-05
Of your laptop... Brand of the PC (or motherboard's) and model (or motherboard's).

---

### Post by arron.faulkner on 2014-10-05
Not a laptop, the brand of the motherboard is gigabyte, that's as much as i know.

---

### Post by Vladlenin5000 on 2014-10-05
Do you know at least whether or not it has UEFI?

---

### Post by arron.faulkner on 2014-10-05
No UEFI

---

### Post by Vladlenin5000 on 2014-10-05
> **arron.faulkner said:**
> No UEFI

Good as that simplify things.
Have you tried with a DVD already? If so was the symptom the same?
There are other tools like Unebootin that may work in systems where others don't. However, before going any further, take a look at this [http://www.linuxliveusb.com/en/help/faq/boot/54-my-usb-device-does-not-boot](http://www.linuxliveusb.com/en/help/faq/boot/54-my-usb-device-does-not-boot) and try other USB options.

---

### Post by arron.faulkner on 2014-10-05
OK, im going to try using a different USB Mode, then using UnetBootin, unfortunately using a DVD is not a option, will keep you updated.

Edit 1: Different USB Mode - Fail, using LiLi

Testing UnetBootin now!

Edit 2: UnetBootin waws ineffective. - Doesnt work

---

