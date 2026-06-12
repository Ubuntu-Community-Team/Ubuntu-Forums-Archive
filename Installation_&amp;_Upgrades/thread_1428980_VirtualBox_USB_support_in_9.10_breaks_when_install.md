---
title: "VirtualBox USB support in 9.10 breaks when installing updates"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by geirgp on 2010-03-13
To keep up with latest patches and stuff, I executed..

```
apt-get update && apt-get upgrade
```

..on my Karmic Koala which I use to run a bunch of VirtualBox VMs. 

After rebooting (kernel was upgraded) I found that VirtualBox was unable to start any VMs due to missing kernel modules. Fixed that by executing:

```
/etc/init.d/vboxdrv setup
```

The VMs will now start up and work, however they are no longer capable of using any USB devices, a complete blocker for me as I have an external 1.5TB disk that I need to access from one of the VMs. 

When I hover the mouse over the USB-icon in the VM-window it displays "No USB devices attached". If i click, the list of USB devices pops up, but they are all grayed out soI cannot manually attach them to the VM.

I had the same problem when I initially set up 9.10 and VirtualBox, but fixed the problem by adding my user account to the "vboxusers" group (gid 121) and appending the following line to /etc/fstab:
```
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0

```

Obviously that is not going to work this time around since it has already been done..

Anyone got some clues on how to fix this?


Thanks,
Geir


edit:typos

---

