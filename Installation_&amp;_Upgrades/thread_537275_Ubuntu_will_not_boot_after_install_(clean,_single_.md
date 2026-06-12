---
title: "Ubuntu will not boot after install (clean, single boot install)"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by eholman on 2007-08-28
I have downloaded ubuntu-7.04-desktop-i386.iso, burned the CD, and verified the CD. I am installing the OS on a clean hard drive, single boot configuration. The installation is successful, but upon reboot I am greeted with a flashing, underscore type cursor.

No error messages, no text, no nothing other than the cursor.

This is a new computer, Asus P5B deluxe motherboard, 4BG ram.

I am fairly adept with computers having been a Windows geek for 10+ years, but a noob to Linux/Ubuntu. With no error message to go on there's not much to Google. Where do I go or what do I do as step one to troubleshoot this?

-EHolman

---

### Post by MetalMusicAddict on 2007-08-28
This does sound odd. Have you tried another install? Maybe something went wrong then? Whats your GFX card? At the cursor try hitting Alt+F2 and see if it puts you at a prompt. Is this laptop "docked"? ie: One of those docks that let you quickly connect it to peripherals?

---

### Post by eholman on 2007-08-28
I've performed the install twice, same result both times. My video card is an Asus NVIDIA GeForce 8500 GT, and I have two of them installed on the motherboard. This is a desktop machine, not a laptop.

I tried the Alt-F2 thing, and get no response. The cursor just keeps flashing in its postion.

---

### Post by MetalMusicAddict on 2007-08-28
> **eholman said:**
> I've performed the install twice, same result both times. My video card is an Asus NVIDIA GeForce 8500 GT, and I have two of them installed on the motherboard. This is a desktop machine, not a laptop.

I tried the Alt-F2 thing, and get no response. The cursor just keeps flashing in its postion.

Do you have PCI-IDE or SATA controllers? Is the drive SATA or ATA?

---

### Post by eholman on 2007-08-28
The motherboard has an Intel P965 chipset and associated SATA controller. The drive is a 160GM SATA hard drive.

---

### Post by Pumalite on 2007-08-28
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62135](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62135)

[http://kerneltrap.org/node/7020](http://kerneltrap.org/node/7020)

[http://kerneltrap.org/node/7077](http://kerneltrap.org/node/7077)

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

---

### Post by eholman on 2007-08-30
Okay, in English this means, what? I'm out of luck and I can just go down the road again with Windoze...

---

### Post by Pumalite on 2007-08-30
I use Intel D975XBX and have had no problems.

---

