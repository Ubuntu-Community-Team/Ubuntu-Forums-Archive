---
title: "Great way to install in multiple systems [.iso from USB.]"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-12-18
After installing Karmic I created a USB Startup Disk and rebooted to it. while In USB Ubuntu, I had made some changes such as ccsm coniguration, saving a file in the Documents folder etc. They were available after another reboot.

My question is, if the files and modifications could be retained/saved in the live Ubuntu in the USB, is not it possible to install applications into it. My idea is to have an Ubuntu system that supports mp3, DVD etc from the startup itself. The same could be used to install the Complete Ubuntu to many PCs.

Please confirm whether it is possible ? If yes tell me how to create an .iso image of this USB.

AptOncd is not an answer as it only backs up the .deb files.

Thanks in advance.

---

### Post by c9-3Rr0r on 2009-12-18
I think that is possible, but I can't check it atm, because I don't have any bootable USB pendrive, so u should try by yourself.

To create a ISO from usb drive, unmount it and then
```

dd if=/dev/sdb of=filename.iso

```

change sdb to your pendrive name.

---

### Post by Cheesemill on 2009-12-18
Or you could just use [Remastersys]("http://geekconnection.org/remastersys/remastersystool.html") to create your own custom installation CD

---

