---
title: "Cannot install Ubuntu Lucid Lynx or Natty Narwhal"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by raymundplaza on 2011-05-09
I created an installation CD and even a usb stick of Ubuntu Lucid Lynx and Natty Narwhal and I keep having freezes during installation. Help! Thanks!

1. Set my BIOS to boot on CD/ usb stick
2. My computer starts to boot from CD/ usb stick
3. Ubuntu logo plus 5 dots screen shown
4. After that I am shown a snowy green screen with white lines running lengthwise and it freezes.

I already tried creating  a new CD and usb stick after re-downloading the .iso installation file and creating the process of creating an installer over and over but still the same problem. Is it a hardware problem or my installer is the problem. I tried installing my old CD of Ubuntu Jaunty that I requested from Ubuntu a long time ago and I can install it without any problems. I am using Jaunty right now. Thanks!

My hardware:
1. Motherboard: Asrock 4CoreDual-Vsta
2. BIOS: American Megatrends Inc. P2.30 (latest version from the manufacturer)
3. CPU: Celeron D 347 (Presler) 3.06GHz
4. Memory: 2GB DDRII533 
5. Monitor: Acer V193HQ (HDMI)
6. Graphics Card: PCI Express NVIDIA GeForce 7200 GS 256MB
7. Mode: 1366x768 with 32 bit color depth
8. Drives: 
8.1  SATA1 - Seagate 250GB (already unpartitioned and unformated using gparted for use for my intended installation of Ubuntu Lucid Lynx)
8.2 SATA2 - Western Digital 320GB (recently installed and unpartitioned, where my Ubuntu Jaunty is installed)
8.3 SONY CD-RW 
8.4SONY DVD-RW
9. OS: Ubuntu Linux 9.04 (Jaunty)

---

### Post by Rubi1200 on 2011-05-09
Hi and welcome to the forums :-)

Firstly, I want to thank you for trying to provide as much relevant information as possible; it sets a good example that others should try and follow.

Okay, to business:

check the integrity first:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

after that, have you tried using nomodeset as a boot option with the LiveCD?
[http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset](http://ubuntuforums.org/showthread.php?t=1613132&highlight=nomodeset)

Give that a go too and let us know what happens.

---

### Post by raymundplaza on 2011-05-11
my md5sum check is a failure. The problem is the integrity of my download. tsk. I guess I have to download it again.  Thanks.

---

### Post by Rubi1200 on 2011-05-11
Download the image again and check the integrity before burning to CD. When you do burn, make sure it is at the lowest possible speed allowed by your burning software.

Then, try to boot the CD again, setting nomodeset if needs be as described in the other link I provided.

Good luck :-)

---

