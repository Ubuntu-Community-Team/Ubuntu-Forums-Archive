---
title: "Keyboard failure at login prompt."
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by wstiern on 2007-10-10
I have a brand spankin' new Dell PowerEdge 2950 that should be running Ubuntu with VMWare Server.

Installation of 7.04 goes fine. At the login prompt, the bloody keyboard stops working.

I've tried both the Server and Alternate ISOs, and get no responce from the GUI or CLI login prompts. The mouse doesn't work at the GUI prompt either.

There are no options in the BIOS for legacy USB support, and the server doesn't have PS/2 jacks anyway.

I've booted into Dell's Server Assistant mini-Linux shell and keyboard/mouse work fine.

The keyboard also functions whilst operating in the BIOS, SCSI controller configuration, and GRUB.

I've tried setting the keyboard manually to both US and US:INTL, and running the keyboard through the detection process during installation.

This is a brand new, generic USB Windows keyboard. I had a mate plug in his Mac external USB keyboard at the prompt just for kicks and it didn't respond either. I'm not sure if the differences between the two are significant enough that a carriage return from one wouldn't send the same zeroes and ones as the other.

Obviously the keyboard itself isn't the problem. I replug it to another jack and the Caps/Num/Scroll lights blink once, as per usual.

I have installed Debian Etch and the keyboard and mouse work fine. I can also boot into the Ubuntu Live CD and the keyboard and mouse work fine.

I spent most of yesterday scouring the 'Net with Google about these issues and have also reviewed every thread in this forum with the word "keyboard" in it. There doesn't seem to be a fix for this issue beyond the BIOS settings or some sort of supernatural intervention whilst replugging the keyboard at random.

Anything anyone could suggest to get the keyboard so I can make use of this expensive piece of hardware with Ubuntu would be greatly appreciated.

---

### Post by wpshooter on 2007-10-12
Have you checked to make sure that the parameters in the BIOS regarding the USB device support are ALL properly set/enabled ?

Have you tried setting ALL of the BIOS parameters to the defaults/failsafe settings ?

Have you check to see if there is available and that you may possibly need an update/flash of your BIOS to the latest and greatest version ?

P.S. - Have you tried blowing some canned air into both the keyboard UBS plug and the motherboard USB ports to get any particles of dust/dirt/trash out of them ?

---

