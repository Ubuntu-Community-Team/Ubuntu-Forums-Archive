---
title: "Cannot Install on Toshiba L505"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by jeffreyldavidson on 2010-05-29
I have the Toshiba L505 with Intel processor. When trying to install it will hang at kernel_thread_helper. If I select acpi=off it will go through the install process until it get 93% and hangs on hardware detection. I am assuming it has something to do with the Linux kernel because I have tried other distros -- Mint, Arch, PCLinux and they all do the same thing. I would prefer Ubuntu if I could just get it to insatll. Help please.

---

### Post by davidmohammed on 2010-05-29
can you start it with livecd?  if so, can you do a lspci and dump the contents here?

Also, try not have a usb devices connected.

You might want to try booting/installing with combinations of nomodeset, acpi=off, noapic, nolapic.

---

### Post by jeffreyldavidson on 2010-05-29
I can get the Live CD to boot as long as the acpi=off is selected. However, my mouse goes crazy all over the screen and the wifi will not recognize my wireless but it does see others which is strange. I have used Ubuntu since Warty and have never had any problem installing on numerous machines and laptops. This is the first this as ever happened.

---

### Post by davidmohammed on 2010-05-29
are you installing lucid 64bit or lucid 32bit?  If 64bit try 32bit and visa-versa.

possibly you are affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183") - looks like there is a possible fix

---

### Post by bbmadzky on 2010-06-07
[B]I have a Toshiba Satellite L505 (with Intel Core 2 Duo processor and 3GB Ram) and successfully installed Ubuntu Lucid Lynx. But I didn't used the desktop Ubuntu, instead I used the Netbook Remix. I used a windows installer. Installation was smooth and fine.
[/B]

---

