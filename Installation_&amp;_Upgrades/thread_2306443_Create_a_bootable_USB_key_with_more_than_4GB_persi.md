---
title: "Create a bootable USB key with more than 4GB persistent storage"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by Gijsbert_Wiesenekk on 2015-12-15
Hi,

I wanted to create a bootable Ubuntu 14.04 USB key with more than 4GB persistent storage. This turned out to be not easy at all: I have tried all possible combinations of MBR/GPT formatted USB keys with all possible combinations of Ubuntu Startup Disk Creator/Universal-USB-Installer/Unetbootin but either the resulting USB key would not boot (the infamous initramfs error) or the persistent storage was still limited to 4GB or the persistent storage would not work (either the casper-rw file or the casper-rw/live-rw labeled partition).
What worked like a charm however was the suggestion I found on the Internet to create as root a Virtualbox VM that boots from the Live ISO image with the USB key attached as a physical disk, so:
```
$ sudo virtualbox
```

Create a new virtual machine with 2GB of RAM without a harddisk. Create a vmdk that maps to the USB key:
```
$ sudo VBoxManage internalcommands createrawvmdk -filename <path-to-VM-directory>/<name-of-vmdk>.vmdk -rawdisk /dev/<device-name-of-USB-key>
```
Attach the vmdk to the SATA controller of the VM, boot the VM and install Ubuntu on the harddisk.

Regards,
Gijsbert

---

### Post by sudodus on 2015-12-15
Thanks for sharing your solution :KS I think it is a good method to use ***virtualbox*** for this purpose.

I have a question:

- Why are you running ***virtualbox*** with sudo? I don't think you need elevated permissions, (and you should use gksudo or sudo -H with GUI applications, otherwise you might get problems with ownership in your home folder).

and a comment:

- You can make a bootable USB key with more than 4GB persistent storage with [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent), and I think it is an easy method.

---

### Post by Gijsbert_Wiesenekk on 2016-01-08
Hi,

The reason for running virtualbox with sudo is that
$ VBoxManage internalcommands createrawvmdk
requires root privileges and I could not access the created vmdk from my account (even after chmod-ing/chown-ing it).

I did not try mkusb/persistent, but I like the virtualbox method. You can even create a fully encrypted bootable USB key that will prompt for password at boot in this way (see my other post).

Regards,
Gijsbert

---

### Post by sudodus on 2016-01-08
I see your reasons for doing it this way :-)

---

