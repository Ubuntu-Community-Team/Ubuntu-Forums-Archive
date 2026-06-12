---
title: "Using a portable live Ubuntu SD card with my Surface Pro 2"
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by geoffroy2018 on 2018-08-08
Good afternoon to all,

I am relatively junior in using linux but I have used a number of tools and built my own PCs before.  I would like to create a Ubuntu Live SD card that would have a profile for permanency and updates.  I use the latest LTS iso and have checked the file and the signatures as advised.  It is a healthy one!

I would like to run it from a Microsoft Surface Pro 2.  So far I have tried the regular install route but I would rather have a Ubuntu Live than a regular install.  I have used Rufus to generate the Live SD and have then tried to boot using that SD card (whether MBR or GPT) with the volume down + power buttons it did not work.  If I create a USB drive using Rufus it boots without a problem. I really wanted to try and rely on the available info and not go to the community right away.  After four late nights I think I am really missing some key elements here.  The SD card and the USB key have exactly the same file structure and info for they are both produced in the same way.  I really do not understand where the issue is.

Please note that on the Surface Pro 2 you cannot select the boot order but only decide whether you start with the SSD or the USB drive / Device.

Any help would be greatly appreciated!

Once I understand the procedure fully I will then do the same on other machines.

I thank you in advance for your responses.

kind regards

Geoffroy

---

### Post by sudodus on 2018-08-08
Are you trying to boot from a built-in slot for a memory card? Is that slot connected via USB or PCI?

Or are you trying to boot from a USB adapter for memory cards?

[hr][/hr]
Some, but far from all built-in slots for memory cards are available for booting.

Many, but not all USB adapters for memory cards are compatible enough with the computer's USB system, to be available for booting. One computer works with some adapters. One adapter works with some computers.

---

### Post by geoffroy2018 on 2018-08-08
I am trying to boot from the tablet/laptop's SD card reader rather than a usb connected SD card reader.  it seems that on the other surface tablets it is part of the USB boot.  I think it is connected to the USB for when I try to boot via usb it shows:  USB & USB class device (I assume this is the SD card).


I see, I might just have a hardware that cannot do that.

---

### Post by sudodus on 2018-08-08
Yes, you might just have a hardware that cannot do that. I don't know how the card reader of Surface Pro 2 is configured, but it is not common, that they are bootable. (I have an Intel NUC with a bootable built-in card reader.)

Maybe you can borrow a USB adapter for your card, and if you are lucky, it will let you boot from the card. Otherwise you can get a cheap USB pendrive with at least 2 GB for a live-only drive or [I would recommend] a fast USB 3 pendrive with at least 16 GB for a persistent live drive or an installed system (in the USB drive).

See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by geoffroy2018 on 2018-08-08
Thank you for this.  Are USB drive still prone to the worms/viruses that hide within usb chips?

---

### Post by sudodus on 2018-08-08
I think there is a problem, but I don't think I have been affected yet, and I don't know any other persons, that have been affected (or know that they have been affected), so I think it is a small problem. By the way, I *think* that memory cards would be vulnerable to the same malware.

---

### Post by geoffroy2018 on 2018-08-08
Hmmm I was thinking about using the "writing blocked" switched for this.  I will look into this.  No need to spend hours trying to solve this if it is not useful in the first place.

---

### Post by sudodus on 2018-08-08
If you have a **live-only** system on the card or USB pendrive, the Ubuntu system will be protected, particularly if you use a cloning tool to create it.

'Writing blocked' means that you cannot store anything on the drive, and only a live-only system will work that way.

Malware that attacks the USB drive's internal system (not the partition table and not a file system) are probably more difficult to check from Ubuntu. I'm not sure if 'Writing blocked' will block such malware.

But if you stay away from web sites, that have a bad reputation, or that you suspect are unsafe, the risk is rather small.

---

### Post by geoffroy2018 on 2018-08-08
Noted!  What about live-only plus a profile to keep portable apps and data in?

---

### Post by sudodus on 2018-08-08
You can install [mkusb](https://help.ubuntu.com/community/mkusb) from a PPA (into one system) and use it to **create a persistent live drive** with Ubuntu or Ubuntu community flavour (Lubuntu, Ubuntu Budgie, Ubuntu MATE, ... Xubuntu) in another drive.

1. **When you want persistence**, you select it at the grub menu. Then you can install and keep portable apps and data files.

```
Run Ubuntu - persistent live
```
or
```
Ubuntu ... - persistent live
```

2. **When you want a live-only system** (where no apps and no data files survive reboot (or shutdown + boot), you select it at the grub menu.

```
Try Ubuntu without installing
```
or
```
Ubuntu ... - live
```

---

### Post by C.S.Cameron on 2018-08-08
Perhaps a UEFI problem? [https://ubuntuforums.org/showthread.php?t=2310300](https://ubuntuforums.org/showthread.php?t=2310300)

---

