---
title: "can not mount on /dev/loop0 on /cow"
date: 2022-09-17
forum: Installation &amp; Upgrades
---

### Post by ssilly-bbilly on 2022-09-17
I am booting from a usb on a HP G61-410SA, which i have seen work before, however the boot fails to "mount on /dev/loop0 on /cow", sending me to the (initramfs) console.
i am very, very new to Linux/Ubuntu, and i have not found an effective solution anywhere else on the internet. 
Maybe it just doesn't work on the laptop, which is an answer i will take as well.

---

### Post by TheFu on 2022-09-17
snap packages use loop devices.  If there are any snaps, those get mounted as loop1, loop2, loop3, loop4, .... loop99.  So, if a loop device is already taken, you can't use it.

This is just a guess. I don't have any clue, since I don't know what /COW has as a special meaning.

---

### Post by yancek on 2022-09-18
Are you trying to boot from an Ubuntu iso you put on the usb?  The message and similar messages you see with 'cow' generally mean trying to write to the system on the usb which won't work as it is a read only filesystem.  I would not expect to see that when simply trying to boot.

---

### Post by sudodus on 2022-09-18
In a USB boot drive /cow 'copy on write' is the 'device name' of the root partition in a current version of Ubuntu live. You should not try to mount that on /dev/loop1. If the system tries to do that, your system is not working correctly.

Please tell us more details about your system:

- which version (22.04.1 LTS?) and flavour is it (Ubuntu Desktop, Ubuntu Server, or a community flavour (Kubuntu, Lubuntu ... Xubuntu) you are trying to use?

- how did you create the USB boot drive (method, tool)?

---

### Post by ssilly-bbilly on 2022-09-18
i am attempting to boot ubuntu 22.04.1 LTS desktop, and i created ths usb with Universal USB Installer 2.0.1.4a.

---

### Post by TheFu on 2022-09-18
> **ssilly-bbilly said:**
> i am attempting to boot ubuntu 22.04.1 LTS desktop, and i created ths usb with Universal USB Installer 2.0.1.4a.

Did you actually do the install from the USB device onto real storage?  Placing an ISO file onto a flash drive isn't really the OS installation. It is preliminary work so that an install CAN be performed off the flash drive.

---

### Post by ssilly-bbilly on 2022-09-18
no, thats the problem. it wont install from the flash drive.

---

### Post by TheFu on 2022-09-18
> **ssilly-bbilly said:**
> no, thats the problem. it wont install from the flash drive.

Ah ... I though you were manually trying to manually mount, not just stuck in some installation problem.
Does the "Try Ubuntu" mode work?  If so, use that and gather some information.  Install inxi (it is only there until the Try Ubuntu environment is rebooted), open a terminal, and run:
```
$ inxi -Fxxxz
```
copy/paste the exact command line and output back here.  After you paste it, use the forum Advanced Editor, select all that text and click on the '#' button. This will wrap that in 'code-tags', so everything lines up.

Or you can download the system-info script, then run it.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)  There are detailed instructions there.

By having an overview of your hardware, someone might see some known issues and make suggestions.  If it is a store-bought computer with a brand and model number, google the "brand + model + ubuntu 22.04 install" <-- obviously put the actual model and brand into the search.  That will often find specific tips necessary for that model to install ubuntu.  This happens more on laptops, but some brands have funky BIOSes and need a little help to install.

---

### Post by ssilly-bbilly on 2022-09-18
i have fixed this by using BalanaEtcher instead to create the bootable usb, thanks for the help though.

---

