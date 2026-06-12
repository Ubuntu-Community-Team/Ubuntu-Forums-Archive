---
title: "cant install ubuntu  error; [(initramfs) mount: mounting /dev/loop0]"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by dimitriosk-dimou on 2014-12-21
Hi everyone,

Every time I try to install almost any version and flavour of ubuntu, on UEFI or on legacy, the following error comes up after choosing ''Try ubuntu without installing''

```
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid argument can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)
```
I tried install the software using a sandisk extreme 16GB 3.0 usb, a kingston 4GB 2.0 usb and the Universal-USB-Installer-1.9.5.8.

Any ideas or questions?

---

### Post by ubfan1 on 2014-12-22
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

I have never used the universal USB installer, but did use unetbootin once (pre UEFI) and it worked.

---

### Post by dimitriosk-dimou on 2014-12-25
Hello ubfan1 and thank you for your response!

I am answering your questions with the given order.
1)Done and everything was fine.
2)Do not have CD/DVD device.
3)if you mean the option ''check disk for errors'' in the menu with ''try ubuntu without installing'' etc, yes i did it and i got the same error.
4)yes
I used both universal USB installer and unetbootin and got the same error.
Something i forgot to mention is that the only flavour that leads to a graphical environment is Xubuntu but installation crashes when '' [FONT=Ubuntu Mono]grub-install dummy failed. This is a fatal error.[/FONT][FONT=Ubuntu Mono]''

[/FONT]

---

