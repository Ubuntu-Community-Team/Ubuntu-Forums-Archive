---
title: "Cannot Boot From USB Kubuntu 20.04_Live_x64"
date: 2024-10-20
forum: Installation &amp; Upgrades
---

### Post by jonnyalpha2 on 2024-10-20
Hi,

Completely new to Ubuntu (but have been using a Raspberry Pi for a number of years).

I have a couple of old PCs with windows 7 on that I use for playing a mix of old PC Games . I recently re-imaged one but have lost the CD key and cannot activate the version of Windows. After some reading on alternatives, I decided to switch to Ubuntu or at least a flavour of it, to play these PC games.

I have opted for Kubuntu and I am trying to follow [this guide]("https://userbase.kde.org/Kubuntu/Installation#") to install the OS to a UBS stick and run it / or install it from there onto one of my PCs.

I have downloaded Kubuntu 24.04.1 and then as stated in the guide I have downloaded Unetbootin to create the USB Boot Drive.
When starting Unetbootin the and have tried using "Distribution", which only offers v20.04_Live_x64 to download and create a bootable USB stick,
I started my PC and selected USB as the Boot device, however when I restart my PC it does not recognise the USB stick as a bootable?

The USB Drive is a Sandisk 64GB - incidentally when I boot into windows, it is not visible in File Explorer, but does appear as a device in Computer / Manage.
I know Chrome OS Flex does not like Sandisk USB Sticks for Boot Devices, is Ubuntu the same?




What am I doing wrong?

---

### Post by Rubi1200 on 2024-10-20
Try Rufus instead:
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

---

### Post by jonnyalpha2 on 2024-10-20
Tried a couple of different things.
This time I used Balena Etcher as mentioned here.
I also used a PNY 64GB Stick instead.

This time pressing F11 on the keyboard and selecting USB I managed to get the initial Kubuntu menu (install / try etc). 
I selected Try and "Kubuntu 24.01" appeared on the screen with three white dots that change to blue. This just stayed there for a couple of minutes and did not seem to be moving on. Anyway I was late so I powered off and will try again in the morning.

---

### Post by jonnyalpha2 on 2024-10-20
> **Rubi1200 said:**
> Try Rufus instead:
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

Sorry - was in the middle of posting a reply when this popped up.
I am on a Mac so could not try Rufus (although I do have a spare Windows Laptop. Anyway read my other reply.

---

### Post by jonnyalpha2 on 2024-10-21
So I have been doing some more testing. Tried again this morning to boot on the PC using the OS imaged to the PNY Mem Stick, same issue.
I then tried on my Windows Laptop and after a while I was in the Kubuntu Plasma Desktop, so it appears to be a PC specific fault?

On the PC this morning I did manage at one point to get the Kubuntu log on the screen, showing on the device splash screen, but then nothing happened afterwards.

The PC specs are:
[COLOR=#32454E][FONT=&quot]Motherboard - ASRock FM2A75M-DGS [/FONT][/COLOR]
[COLOR=#32454E][FONT=&quot]CPU - AMD A6-5400K[/FONT][/COLOR]
[COLOR=#32454E][FONT=&quot]Mem - 8GB Ballistix[/FONT][/COLOR]
[COLOR=#32454E][FONT=&quot]Gfx Onboard - Radeon HD Gfx[/FONT][/COLOR]
[COLOR=#32454E][FONT=&quot]Gfx PCiE - ASUS GTX 750Ti[/FONT][/COLOR] 

I have been into UEFI / BIOS and checked legacy USB is enabled and I am using a rear panel USB socket.

The PC recognises the USB stick and I get the install / try Kubuntu menu
I select try/install and the screen goes blck with a cursor top right, that disappears, then nothing display is disabled.
Maybe I'll disconnect the Nvidia Graphics card and use the onboard only and see what happens?

Did that and now I seem to be into the Kubuntu Desktop.

So this was a Gfx problem.

---

### Post by Rubi1200 on 2024-10-21
I don't have Nvidia on any of my machines but there are plenty of threads here that discuss problems with graphics.

Good that you got it sorted for now.

Please mark as Solved using the Thread Tools at the top of your first post. It may help others facing this issue.

Thanks

---

