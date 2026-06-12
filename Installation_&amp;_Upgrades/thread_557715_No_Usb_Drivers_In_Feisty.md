---
title: "No Usb Drivers In Feisty"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by always lost on 2007-09-23
[SIZE="6"]I can't get my usb flash drive to be recognized in Feisty. Even tried to install the windows version using 'wine'. Nothing..... doesn't even appear in the system. Where do I get the drivers ?????    Ian:p

---

### Post by linuxwizard on 2007-09-23
[https://help.ubuntu.com/community/UsbFlashDrives](https://help.ubuntu.com/community/UsbFlashDrives)

---

### Post by cowkiller on 2007-09-23
> I can't get my usb flash drive to be recognized in Feisty. Even tried to install the windows version using 'wine'. Nothing..... doesn't even appear in the system. Where do I get the drivers ????? Ian

This worked for me in feisty with my external USB HDD, hope you find it useful:

firstly unplug your flash drive from the usb port and type in a command-terminal

```
ls /dev/disk/by-uuid/
```

you'll get a bunch of numbers and letters.. not much important, but keep an eye on them.

Now plug your flash drive and repeat the same operation. If the device was recognised,  you'll see a new file there. Copy it.

Now make a new directory to mout it in /media

```
sudo mkdir /media/usbdisk
```

(actually you can name it whatever you want instead "usbdisk", this name's just an example).

and mount the device

```
sudo mount /dev/disk/by-uuid/xxxxxxxxxx /media/usbdisk
```

where xxxxxxxxxxx must be the ID you copied before from the /dev/disk/by-uuid directory.
This should make it work

Hope it solved your issue, good luck! and please give some feedback

---

