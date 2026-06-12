---
title: "Boot from SD Card"
date: 2017-05-23
forum: Installation &amp; Upgrades
---

### Post by brett7481 on 2017-05-23
Hey,

Just got a new HP Stream 11. I would like to be able to dual boot and run Ubuntu from a 64 GB SD card. Problem is, the stream won't boot from the SD Card slot. I've read about creating a 500 MB boot partition on the main SSD and installing the rest on the SD...

This article seems to describe this:
[https://help.ubuntu.com/community/BootFromSD](https://help.ubuntu.com/community/BootFromSD)

Problem is, I don't understand most of it, lol. 

Can someone walk me through this in a bit more detail?

---

### Post by oldfred on 2017-05-23
The Stream seems to be a real lightweight system that is difficult to install.
Is it also one that is 32 bit UEFI?
That was Windows solution to make a Windows only system like Ipads are Apple only.
Linux did not have 32 bit UEFI back then, but later release grub/UEFI capability, but not part of any default install. You have to add the 32 bit UEFI file(s).

Do not know details, but another thread.
 Linux on the HP Stream tablet
[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188)

---

### Post by efflandt on 2017-05-24
Whether you would be able to boot from the SD card slot may depend upon how it is internally connected. It should be able to boot from the slot if is internally USB connected, but maybe not if it is a different type of block device. Most laptops cannot boot from their SD slot, but I have an older 10.1" tablet PC with detachable keyboard (that came with Win7 Pro on 32 GB SSD) that can boot from its internally USB connected SD slot, but limited to 32 GB allegedly (I have not tested it with SDXC). Although, newer computers should support larger SDXC and even my 7 year old desktop PC can access SDXC (with exfat-utils package installed) on its internally USB connected card reader.

The output of lspci and lsusb from live/install system might help identify how your SD card slot is connected.

---

### Post by LastDino on 2017-05-24
Couple of years ago I used to only use SD cards to install and repairs, they were easily accessible as I was carrying them with phone and had a card reader handy in bag. Like effland suggested, your primary action should be finding out how the SD card slot is connected to core system. If it is not USB connected internally, you can easily use USB card reader available for less than a dollar or two for this purpose.

---

