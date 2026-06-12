---
title: "I can't install Ubuntu from usb"
date: 2023-01-28
forum: Installation &amp; Upgrades
---

### Post by crackoffbird on 2023-01-28
I've been using Zorin OS on my laptop and now I decided I want to install Ubuntu instead. I made a boot pendrive with balena etcher and went for it. I selected the USB at the boot order but then it displays "GRUB" and nothing else. Then nothing happens.
Could you help me with this or ask for further info please?
Thanks

SOLVED: used UNetbootin to make the usb

---

### Post by sudodus on 2023-01-28
- Please tell us about your computer: Brand name and model
. of the computer itself and
- of the graphics chip/card.

- Tell us which iso file you downloaded and used to make a USB boot drive..

- Did you check with sha256sum, that the download was good?

- Can you check if your computer boots in UEFI mode or BIOS mode (alias CSM alias legacy mode)?

- Can you still boot your computer into Zorin? In that case, please download and run the [system-info script](https://github.com/UbuntuForums/system-info/). Let it upload the result to a pastebin and post a link to the pastebin so that we can learn about the details of your computer.

- Can you boot some other computer with your USB boot drive with Ubuntu?

---

### Post by crackoffbird on 2023-01-28
here is the system info: [https://paste.ubuntu.com/p/FzCz3fS8pg/](https://paste.ubuntu.com/p/FzCz3fS8pg/)
I downloaded the 22.04 LTS version.
I did not check it with sha256sum.
I'm not sure, but I think it boots in bios mode.
I can boot other computers with it.

---

### Post by sudodus on 2023-01-28
Thanks for the uploaded result from the system-info script :-)

It will make it much easier to help you. (If I fail, there are others who will identify what is problematic and what to try in order to solve the problem.)

The fact that you can boot other computers tells us that the USB boot drive is good.

[hr][/hr]
You have an old HP notebook with a second generation Intel i5 CPU launched during 2012
and Radeon HD 6400M/7400M graphics.

[SIZE=3]Possible boot problem[/SIZE]

I know that some HP computers from that period can be difficult to boot from USB, particularly if the drive 'looks like it has a GUID partition table', GPT.

This might be worked around, if you use [Rufus](https://rufus.ie) instead of a cloning tool. (Rufus needs Windows.) 

You can also try with [mkusb-dus](https://help.ubuntu.com/community/mkusb) in Zorin, and make a persistent live drive (not a cloned live-only drive). But there might be problems during installation from a persistent live drive, so follow the instructions at [this link](https://help.ubuntu.com/community/mkusb/persistent#The_installer_Ubiquity_in_most_Ubuntu_flavours): boot with toram and swapoff everything in the live system before you start the installer. You can also try with Unetbootin.

[SIZE=3]Possible graphics problem[/SIZE]

I would not think so, but there might be a regression with the graphics driver (that the current default driver in Ubuntu 22.04 cannot manage your graphics card). In order to check that, the first thing to test would be to try with the boot option **[FONT=Courier New]nomodeset[/FONT]**, which you get in 'recovery mode' (or can set manually in the grub menu).

[hr][/hr]
Edit 1: It might also be a good idea to try a community flavour of Ubuntu with a lighter desktop environment, Lubuntu, Ubuntu MATE or Xubuntu. They all use different desktop environments, that are better for old hardware, but they use Ubuntu's graphics drivers. Lubuntu is also using a different installer, Calamares, which could be better or worse with your particular hardware configuration.

It might also be worthwhile to try the previous LTS version, Ubuntu 20.04.x LTS. It might manage your computer's hardware better than 22.04.x LTS, and the life-time is 5 years, so you get security and other updates (of 20.04.x LTS) until April 2025.

Edit 2: I notice (in the system-info pastebin) that you have the gezakovacs-ubuntu-ppa. It indicates that you have Unetbootin, and it might also be able to make the USB pendrive bootable for your computer.

---

### Post by crackoffbird on 2023-01-29
I tried making the USB with UNetbootin and it worked flawlessly! 
Thank you so much!&#128578;

---

### Post by mIk3_08 on 2023-01-30
> **crackoffbird said:**
> I tried making the USB with UNetbootin and it worked flawlessly! 
Thank you so much!&#128578;

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

