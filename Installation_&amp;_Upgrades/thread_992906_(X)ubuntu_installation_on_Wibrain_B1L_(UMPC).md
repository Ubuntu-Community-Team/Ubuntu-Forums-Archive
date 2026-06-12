---
title: "(X)ubuntu installation on Wibrain B1L (UMPC)"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by hyperion51 on 2008-11-25
I have recently wanted to get Linux back on my Wibrain, which came with it preinstalled, but I decided to go for Windows instead. Since the Wibrain does not come with a CD drive, I've had to resort to the several methods of USB installation, all of which work well in theory, but there have been problems.

At first I experimented with persistent Live USB Distros. Both DSL and Pendrivelinux work well enough, but drivers for the Wibrain only come in the Ubuntu flavour, and PDL does not accept .deb's, only .rpm's. So I had to try Ubuntu. 

Trying to boot Ubuntu 8.10 Live, Ubuntu 8.04.1 Live, or Xubuntu 8.10 Live all result in a successfull boot... To a blank screen. Both the vga=771 switch and the (...)pcmcia=false switch have no effect on the blank screen, either. Concerning this problem, I tink I remember getting something like this back when I was running the Ubuntu factory installation. Back then, I think I accidentally switched the primary display to the vga port on the bottom of the Wibrain, and got a blank screen like this one after the automatic reboot. I used the port connected to a projector to fix the problem, but using that port now would require an adapter that got lost during my family's move to Europe. That's probably a long shot here, anyway.

Trying to use one of the Alternate disks (Ubuntu 8.04.1 Alternate or Ubuntu 8.10 Alternate) by converting to usb via unetbootin results in the installer searching and begging fruitlessly for a CD drive with the installation data, which of course is entirely absent, as I'm attempting to do this via USB.

I would love to know how Wibrain (or anyone else) installs Linux on these machines, as I seem to be out of options here.

Any help would be appreciated.

Edit: So far it seems a solution for either
- The Desktop flavour's white screen
- The MID flavour's black screen, or 
- The Alternate flavour's CD crisis
would solve all my troubles for the moment.

---

### Post by hyperion51 on 2008-11-25
> The MID USB image allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This USB image is optimized for handheld devices with 4-7" touchscreens and limited processing power. You will need at least 128MB of RAM to install from this image.
"devices with 4-7" touchscreens and limited processing power", kinda like the Wibrain.

That looked promising, and continued to look promising until after Ubuntu's pretty boot screen, an empty black screen came up, with a DOS-like blinking white cursor at the top left. Now, I'm pretty sure there's a cheatcode that will help me, but they don't teach these things in High School (they should, though). Can anyone help me out on this front?

---

### Post by somnorosul on 2008-12-18
There is an instalation guide for ubuntu 8.04 that i have used and it works.
The problem is that the openchrome does not use the lcd of the video card but switches to the vga port. So in order to install you have to have a monitor and use it.
after the instalation switch to the linux image 2.6.24-16 (I belive) and search on google code for wibrain and you will find downloads for the vidocard wifi and an utility program (to modify the cooler speed and backlight for keyboard etc.)
this will give you full compiz.
I have not find drivers for intrepid yet.
here is the link:
[http://http://code.google.com/p/wibrain-b1l/downloads/list]("http://http://code.google.com/p/wibrain-b1l/downloads/list")

---

### Post by Doctor Colossus on 2009-05-18
> The problem is that the openchrome does not use the lcd of the video card but switches to the vga port. So in order to install you have to have a monitor and use it.

BTW, VGA output can be enabled via Wibrain's BIOS, under 'Advanced'.

---

