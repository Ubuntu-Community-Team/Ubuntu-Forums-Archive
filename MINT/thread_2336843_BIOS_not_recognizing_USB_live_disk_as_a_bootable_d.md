---
title: "BIOS not recognizing USB live disk as a bootable disk"
date: 2016-09-12
forum: MINT
---

### Post by dcolsonvt on 2016-09-12
I'm trying to create an Ubuntu USB live disk. (Not trying to install Ubuntu on my machine, just want to be able to boot into the USB to be able to edit partitions on my machine's main disk). I can't get the BIOS to recognize the live disk as a bootable drive. When I go to change the boot order, there is nothing listed. 

[B]Some information on my machine and what I've done so far:
[/B]
I am using a Samsung Ativ Book 9 Plus, simple specs are here: [http://www.cnet.com/products/samsung-ativ-book-9-plus/specs/](http://www.cnet.com/products/samsung-ativ-book-9-plus/specs/)

I am currently running Linux Mint v17.3. I installed this using a USB live disk of Mint ~8 months ago (yes, I got a live disk working with my computer then). 

I created the Ubuntu disk using UNetBootIn. I tried both downloading Ubuntu through UNetBootIn and installing it using a downloaded iso. 

I've disabled fastboot (which seems to often cause problems for newer hardware). 

All to no avail >_<

If anyone has thoughts or references to other materials, it would be much appreciated!

---

### Post by carl4926 on 2016-09-12
If you are using Mint, why didn't your write the USB with the USB creator in Mint

---

### Post by howefield on 2016-09-12
Thread moved to the "*MINT*" forum.

---

### Post by sudodus on 2016-09-12
Welcome to the Ubuntu Forums :-)

- If you are running in UEFI mode, you need an amd64 alias 64-bit iso file, and please check the following link for information about UEFI (if running in UEFI mode)

```
test -d /sys/firmware/efi && echo efi || echo bios
```

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

- Did you check with md5sum that the download was good? See [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Try to install from the iso file to the USB pendrive with [mkusb](https://help.ubuntu.com/community/mkusb).

- Can you boot another computer from this USB pendrive?

---

