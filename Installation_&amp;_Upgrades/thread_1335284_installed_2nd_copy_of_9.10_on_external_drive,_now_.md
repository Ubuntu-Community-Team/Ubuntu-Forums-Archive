---
title: "installed 2nd copy of 9.10 on external drive, now Grub is broke"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by smapdi636 on 2009-11-23
I have 9.10 installed on my notebook and wanted to install a 2nd copy on a USB external drive so I could test something.  That went fine, however now if the USB drive is disconnected, grub no longer loads. :(  It shows:

```
GRUB loading.
error: no such disk
grub rescue>
```

So I guess now grub is referenced to the external drive and loads only from there.  I am still able to boot to my main instance of 9.10 by having the external USB attached and selecting it from the grub menu.  I would like grub to run off the internal hard drive and have the option THERE to boot to the USB instsance...

What did I do and how do I fix it?

Image attached for your viewing pleasure.

---

### Post by ptn107 on 2009-11-23
Run the following from a live CD terminal, assuming 'sda' is the original internal hard disk:
```
sudo grub-install /dev/sda
```

---

### Post by audiomick on 2009-11-23
Hallo.
If you plug the USB drive back in, does it all work again?

---

### Post by presence1960 on 2009-11-23
It won't boot without the external disk in because when you installed to that external you overwrote GRUB on the internal disk's MBR and now it is pointing to the external for /boot/grub/grub.cfg.

To reinstall GRUB 2 from a Live CD/USB follow [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") taking care to install GRUB 2 to MBR of first internal disk to boot in BIOS.

You can also then install GRUB 2 to MBR of usb external that way when you plug the external in and boot from USB that OS will boot. If you have the external unplugged then the GRUB you restored to your internal disk will take over.

---

### Post by smapdi636 on 2009-11-23
Thanks all ... I'll see how I make out.  Guess I'll attempt this tonight.  I'm too afraid to hose my machine during the day! (at work)

@audiomick  Yes both 9.10 instances are accessible if the USB drive is attached.

---

### Post by namok on 2009-11-23
If you are worried that something goes wrong during installation then download the program [Super Grub Disk.]("http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso") To run Ubuntu just start the computer from the cd and select the following menu:```
1. Choose Language & NO HELP
2. English Super Grub Disk
3. Gnu/Linux
4. Boot Gnu/Linux
5. Boot Gnu/Linux Directly

```

---

### Post by smapdi636 on 2009-11-23
Thank you all!  presence1960's instructions worked perfectly and I'm a happy camper again.

I was able to install grub on both the internal and external drive and can boot grub from either.

I had to **sudo update-grub** with the external drive mounted to get an entry in the grub menu for the external drive's 9.10 instance.

---

### Post by presence1960 on 2009-11-24
> **smapdi636 said:**
> Thank you all!  presence1960's instructions worked perfectly and I'm a happy camper again.

I was able to install grub on both the internal and external drive and can boot grub from either.

I had to **sudo update-grub** with the external drive mounted to get an entry in the grub menu for the external drive's 9.10 instance.

Glad you got it working. Enjoy Ubuntu.

---

