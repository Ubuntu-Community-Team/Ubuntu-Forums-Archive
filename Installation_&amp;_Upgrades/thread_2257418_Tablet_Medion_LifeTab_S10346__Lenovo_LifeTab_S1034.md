---
title: "Tablet: Medion LifeTab S10346 / Lenovo LifeTab S1034x"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by stemuedendron on 2014-12-19
Hello All!

I have an Android tablet, Medion LifeTab S10346 which is really a Lenovo LifeTab S1034x. Its an Intel Atom Z3735F tablet with Android 4.4.

It has an USB-OTG port and I try to boot Ubuntu:
- I have connected a powered USB-Hub to the USB-OTG port
- I have connected a keyboard and an USB-Stick to the hub
- on the stick is ubuntu-14.04-desktop-amd64 (GPT partition with fat32)

Now I can turn the tablet on while pressing Vol+ and Power so it boots in the efi shell. Here I can:

```

map -r //find the stick
fs1: //change to the stick
cd EFI
cd BOOT
grubx64.efi //start grub

```


Now I'm in grub and can use it the usual way and can start booting ubuntu but as soon as I start booting the LEDs on my hub goes out. The linux kernel starts and I see the typically messages on the screen but it can not load the root filesystem and my keyboard is dead so it hangs in a minimal shell.

So my question is:
It is generally possible to boot ubuntu this way or is it impossible what I'm trying?

Thanks!

---

