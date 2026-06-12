---
title: "Problem with installation"
date: 2017-06-19
forum: Installation &amp; Upgrades
---

### Post by lerby on 2017-06-19
It appear almost right after i choose any element in grub menu (both "try without install" and "install" items). [Img]("https://i.imgur.com/OMC2xq8.jpg"). I was waiting about 10 minutes but nothing changed.

Appearance in order:
1) GRUB menu, choosing item;
2) Input strip;
3) Randomly located green and white stripes (i guess it supposed to be something like loading bar?);
4) Nothing happening for about 20-30 sec;
5) This unknown symbols.

Ubuntu was loaded from "http://releases.ubuntu.com/16.04/ubuntu-16.04.2-desktop-amd64.iso", used rufus a few times (with checks for bad sectors).

My specs:
Motherboard: Gigabyte GA-970A-DS3P
CPU: AMD FX-8350
GPU: NVIDIA GeForce GTX 970
RAM: Kingston HyperX (8 GB DDR3)
SSD: Crucial CT256MX
Power Supply: Corsair VS650

Windows 10 installed right now. The problem is probably my PC, but installer must display correct error anyway, right? I can run any needed tests.

---

### Post by ubfan1 on 2017-06-19
Probably a video problem with the Nvidia hardware.  At the grub prompt, type e to edit, and add the word "nomodeset" (no quotes) after the "quiet splash" on the linux line, then boot with ctrl-x or F10.  When running, you can add the proprietary Nvidia drivers from the "software updater" /settings button/ additional drivers tab.

---

### Post by lerby on 2017-06-19
Here is what i've got [img]("https://i.imgur.com/06Eh84V.jpg") (errors)
[Few more tries]("https://imgur.com/a/4pwRu") (different ports were used some times, but not always. Can do more clear tests with different ports if needed).

---

### Post by ubfan1 on 2017-06-20
Maybe too much USB power draw.  See [https://askubuntu.com/questions/341241/ubuntu-wont-start-with-device-descriptor-read-64-error-32-what-does-this-m](https://askubuntu.com/questions/341241/ubuntu-wont-start-with-device-descriptor-read-64-error-32-what-does-this-m)

---

### Post by lerby on 2017-06-21
> **ubfan1 said:**
> Maybe too much USB power draw.  See [https://askubuntu.com/questions/341241/ubuntu-wont-start-with-device-descriptor-read-64-error-32-what-does-this-m](https://askubuntu.com/questions/341241/ubuntu-wont-start-with-device-descriptor-read-64-error-32-what-does-this-m)
Unfortinately that didn't help me. Unplagged everything except keyboard, usb-flash, monitor (not usb ofc, just mean that i really unplagged absolutely everything except this 3 devices). I udnerstand that this right now is not your problem anymore (not ubuntu), but can you help me to solve it please? What else can i do? How to determine broken part of my hardware?

---

### Post by ubfan1 on 2017-06-22
Take a look at the output of lsbusb -t   and see if the problem devices are all off one bus.  But USB hardware problems are pretty basic -- there's probably a peripheral chip that does it, along with a lot of other things like hard disk, wireless, ...  I had a laptop with a heat problem which caused its master peripherial controller chip to crack its solder pads, causing all sorts of problems, among them USB failures.  I went thought three motherboards on that laptop before I got tired and got rid of it.

---

