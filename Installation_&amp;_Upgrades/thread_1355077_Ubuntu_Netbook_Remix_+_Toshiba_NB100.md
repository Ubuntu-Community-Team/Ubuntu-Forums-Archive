---
title: "Ubuntu Netbook Remix + Toshiba NB100"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by lamadredelsapo on 2009-12-14
I'm trying to install ubuntu netbook remix 9.10 in a Toshiba Netbook remix NB100. I made the bootable USB drive, but after pressing "try ubuntu without modifying your computer" or the "install ubuntu option" it won't boot. It just shows a blank screen. I also tried changing the sata mode in the bios from ahci to compatibility mode but i still have the same problem.

Disabling the quiet parameter it shows the following error:

```
Can not mount /dev/loop1 on /cow
```



Anyone had a similar problem? Any idea?

---

### Post by valvegrid on 2009-12-14
Sorry I'm not going to be much help sorting your problem out, but just to reassure you that it should install. I have a Toshiba NB100 and I installed Ubuntu remix 9.10 and everything went well.

In the BIOS I had to just changed the boot order so that it booted from the USB drive.

---

### Post by lamadredelsapo on 2009-12-17
No one knows what the hec means?

```
Can not mount /dev/loop1 on /cow
```

---

### Post by lamadredelsapo on 2009-12-18
It turned out to be a problem with the bootable usb. I initially created it from Windows 7 but it didn't work. I then recreated the bootable usb from ubuntu and it now works.

---

