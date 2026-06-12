---
title: "Can't install ubuntu"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by Monkihunta on 2011-11-15
Hi, I'm currently running Mint helena on my Acer aspireone. I'm trying to install Ubuntu 11.10 from a usb stick, but I'm having problems. I can boot up from the USB, and get to the screen which gives options to install, etc, but when I try to go ahead with the installation, it immediately stalls, giving me a bunch of error messages. Can anyone tell me how I can fix this and get 11.10 installed? Or maybe I'd be better off trying the latest Mint? Would it be possible to install that from a USB?

---

### Post by darkod on 2011-11-15
When you get the menu, hit F6 for advanced options, look around and select nomodeset. Then continue with Try Ubuntu and see if it loads the live mode.

If it did, you can install but on first boot you will have to add nomodeset to the boot commands to allow it to boot. After it has booted once you can look for drivers to install.

Usually it's something with a driver missing.

---

### Post by Monkihunta on 2011-11-15
Hi, thanks a lot for the reply!

I tried again and went into the Advanced Menu. However, there don't appear to be any options in this screen other than 'Back' (weird). If it helps, I took a photo of the error messages:

---

### Post by Rubi1200 on 2011-11-15
How did you put the ISO image on the USB stick?

Please post the specifications for the computer in question, especially RAM and graphics card.

---

### Post by Monkihunta on 2011-11-15
I put the ISO image on the stick with Universal USB Installer as per the instructions on the website./ Strictly speaking its a card reader with a card in it, though have installed Ubuntu using the same hardware in the past.

My hardware:

Acer AspireOne A110L

Specifications (base version)  Manufacturer Acer    Model name Aspire One    Model id A110L    CPU type  Intel Atom (Diamondville)  		       CPU speed 1600 Mhz    Graphics [Intel GMA 950]("http://www.intel.com/products/chipsets/gma950/index.htm")   OS Linux Linpus Lite    Display Size
  8.9" 1024 X 600  Display Type
  LED b/l,   RAM 512 MB (upgraded to 1.5gb)
  Flash 7.8 GB    Keyboard YES   Mouse Pointer YES   Battery capacity 26 (Wh)   Weight 950gm / 33.5 oz.    Size (w/h/d mm) 248/170/29 mm   Size (w/h/d inches) 9.8/6.7/1.1

---

