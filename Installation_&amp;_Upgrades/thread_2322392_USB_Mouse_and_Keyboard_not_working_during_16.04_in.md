---
title: "USB Mouse and Keyboard not working during 16.04 install"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Sean_Ooley on 2016-04-27
I am trying to install 16.04 on my computer. I have a Gigabyte 970A-UD3P motherboard. It is UEFI. I used Parted Magic to create the partitions beforehand, so I know the keyboard and mouse work in all USB ports. When I get into the installation, the mouse and keyboard don't work. If I use "Try Ubuntu" it loads Ubuntu up nicely, but neither the mouse nor keyboard work.

I've used Ubuntu on various machines since 10.04 and this is the first time I've had issues. It's likely a UEFI issue, but since UEFI is so prevalent now, I would think Canonical would have foreseen at least a couple of issues.

Please assist.

---

### Post by RobGoss on 2016-04-27
> **Sean_Ooley said:**
> I am trying to install 16.04 on my computer. I have a Gigabyte 970A-UD3P motherboard. It is UEFI. I used Parted Magic to create the partitions beforehand, so I know the keyboard and mouse work in all USB ports. When I get into the installation, the mouse and keyboard don't work. If I use "Try Ubuntu" it loads Ubuntu up nicely, but neither the mouse nor keyboard work.

I've used Ubuntu on various machines since 10.04 and this is the first time I've had issues. It's likely a UEFI issue, but since UEFI is so prevalent now, I would think Canonical would have foreseen at least a couple of issues.

Please assist.


Hello and welcome, So I'm assuming you did not complete the installation correct?

Try viewing this help gare they have a few things that might help you
[http://askubuntu.com/questions/512430/usb-keyboard-mouse-stopped-working-ubuntu-14-lts](http://askubuntu.com/questions/512430/usb-keyboard-mouse-stopped-working-ubuntu-14-lts)

---

### Post by kurt18947 on 2016-04-27
> **Sean_Ooley said:**
> I am trying to install 16.04 on my computer. **I have a Gigabyte 970A-UD3P motherboard.** It is UEFI. I used Parted Magic to create the partitions beforehand, so I know the keyboard and mouse work in all USB ports. When I get into the installation, the mouse and keyboard don't work. If I use "Try Ubuntu" it loads Ubuntu up nicely, but neither the mouse nor keyboard work.

I've used Ubuntu on various machines since 10.04 and this is the first time I've had issues. It's likely a UEFI issue, but since UEFI is so prevalent now, I would think Canonical would have foreseen at least a couple of issues.

Please assist.

I don't recall details regarding this problem because i don't have a motherboard with the 970 chipset but I recall reading about USB issues. Perhaps if you do a search something like "AMD 970+USB" here or on askubuntu you'll find some info. I seem to recall is has to do with enabling or disabling iommu in the BIOS setup but as I said, I don't recall details.

---

### Post by Sean_Ooley on 2016-04-27
Yah, that doesn't help at all. If the install routine doesn't allow me to use mouse or keyboard, then there is no way I can install it. I tried installing from both DVD and from a USB stick. I find it strange that it accepts the USB stick until the actual install routine opens up asking what language is wanted, but after that, all USB access is turned off.

Again, both keyboard and mouse (and two other mice and one keyboard that are known to work) work inside the bios and while using Parted Magic or any other boot system. It is only Ubuntu that will not recognize my USB ports. UPDATE: I have another computer with an ASUS UEFI motherboard and it does the same thing on that computer as well.

---

### Post by NeilMonday on 2016-05-28
I experience the same problem. Keyboard works fine when selecting the boot device, and even during the DVD's boot menu to "Install Ubuntu". Once the actual installer is running, however, my usb keyboard no longer works. Num Lock key is still lit, but the keyboard does not work at all. This is with an HP Pavilion 550-126. I have tried multiple USB keyboards, and multiple DVD drives, and the same problem with all of them.

---

### Post by NeilMonday on 2016-05-29
Ubuntu 14.04.04 server seems to work just fine, so I will stick with that for now.

---

### Post by DHell on 2016-06-22
I've had similar issues with that same MB + fresh Ubuntu install. In my case it also affected the ethernet port.
The solution for me was to edit a Grub config file -  follow instructions [here]("http://askubuntu.com/questions/769013/ubuntu-lts-16-04-install-problems-uefi-and-black-screen-after-grub-loader") (answer by Steven Carpentier), and good luck!

---

