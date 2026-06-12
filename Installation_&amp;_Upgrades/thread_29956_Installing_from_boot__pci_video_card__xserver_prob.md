---
title: "Installing from boot / pci video card / xserver problem."
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by A-Blue on 2005-04-26
Hello, a few days ago I decided to try out installing Ubuntu on my older system to try it out, I downloaded the iso and burned it properly. The boot cd starts up and installs, and it was giving me No screens found error. The autodetect for video hardware initially installed the drivers as sis, but they don't work, well not properly anyway and I dont even know what sis is, I'm pretty new to linux as well.

I was reading through older posts on here and recommended trying the xserver reconfigure commands, and I reconfigured it to load up with vga drivers, and linux booted to desktop. But of course the way it is set up, looks horrible, and runs terribly slow.

The computer I am running on has a 800mhz processor, 512 ram, and the video card is: "Hercules 3D Prophet 4000x 64mb PCI" when I go to the Hercules site, it only has supported drivers for Mandrake / Redhat / Suse (with notations to help install), and after downloading the normal drivers I am stuck. That site only has one file to download that I found proper to install (which is said to be for all linux systems), but I am not sure how to install it, being use to windows, I would normally look for an executable, or even a batch file but I don't see this in there.. there is a Makefile, with generic extension, but I dont know how to run it, or if that's even the proper file.

I can get the xorg.conf file on here, but I dont know if that would help at all.

Thank you, 

James M~

---

### Post by nad on 2005-04-26
Hi,

Welcome to ubuntu. Please careful of the construction. Things are not 100% around here yet.

Sis is the driver that was automatically selected for you through the video subsystem's probing of your hardware. Apparently that Hercules card has an sis graphics controller chip.

Since you seem comfortable editting configuration files by hand. please post the autoconfigured xorg.conf and your edited files in a code box (<code>....</code>), we will take a look and offer suggestions.

The output of a command line instruction would be helpful also. The command: lspci  will output to your display some information about the hardware that was found on your system.

A detailed description of your problem would also be helpful.

---

