---
title: "Cant make a bootable USB"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Benito Recio Totoro on 2008-03-02
I cant install isolinux in the USB
When y type this command: cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/

The answer is: cp: the destiny, `/media/ubuntu710/', is not a directory: The file or directory does not exist.

I'm new in this software I really dont know how to solve this.

---

### Post by jeffus_il on 2008-03-02
What you are running expects your USB device to be mounted on `/media/ubuntu710/'. Did who miss out a ```
mount
``` command in the guide you are using?

---

### Post by Benito Recio Totoro on 2008-03-02
I'm using this tutorial: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/#more-243](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/#more-243)
I get stuck in number 17, I didnt miss any step i guess; I`ve tried many times and the same happens.
Thanks for helping

---

### Post by jeffus_il on 2008-03-02
type ```
mount
``` in a terminal, the output will tell you if the USB drive is mounted and at what mountpoint (directory, folder)

---

### Post by Benito Recio Totoro on 2008-03-02
i´ve been an idiot all this time, i was partitioning and formating once and once again the hard drive without knowing all this time. Obviously i deleted windows and al my homework and stuff but is OK y learned something and a chance to make all over again but this time the right way. Thanks a lot.

---

