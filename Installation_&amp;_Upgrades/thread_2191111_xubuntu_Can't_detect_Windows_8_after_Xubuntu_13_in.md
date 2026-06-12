---
title: "xubuntu: Can't detect Windows 8 after Xubuntu 13 install"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by chandank.kumar on 2013-12-01
Hello,

This may sound similar question, but looks like my case is little different as the solutions suggested on this forum did not work (boot repair stuff). Basically after running that boot repair it created much or more grub entries but I cant load load it says "cant load image" while it is trying to access the windows Image.

Please find my boot repair log in the paste bin.

[http://pastebin.com/MVjaF92Q](http://pastebin.com/MVjaF92Q)

Also, I have installed in ufi mode 64 bit. And my windows 8 was working without issue before Ubuntu install. Mine is brand new Ace E1 (intel i3) laptop.

I will appreciate for any direction or help I really need this to be dual boot.

---

### Post by Bucky Ball on 2013-12-01
Try this.

Boot from a liveCD, get to a desktop, open a terminal and:

```
sudo grub-install /dev/sda
```

Reboot.

---

### Post by oldfred on 2013-12-01
Boot-Repair will add all efi files found in the efi partition as it does not know which you really need. You can houseclean most of those out of 25_custom. Instruction in link in my signature.

But your BootInfo report is not now showing any boot files in your efi partition. You should have several folders Boot, Microsoft & ubuntu. You show none?
It does look like files were there when Boot-Repair & grub updates ran as it added all the correct entries into grub menu and found efi files.
It also looks like Boot-Repair did some backups, so you may have copies in folders where boot repair saves backups. Not sure what all it saved, but look in /var/log/boot-sav/log.

---

