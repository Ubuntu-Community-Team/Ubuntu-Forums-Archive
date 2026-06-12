---
title: "Help installing Ubuntu --details inside"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Brockoli on 2007-03-06
I've spent many hours now trying to get Ubuntu installed on my pc with very little luck.  Here's a brief update on what hardware I'm looking at and what I've tried so far.

Intel Core2Duo 6400
Asus P5B Deluxe WiFi
1G OCZ Special Ops PC6400 Ram
IDE Pioneer 111D Dvd writer
IDE WD 200G HD
Sata WD 120G HD
Sata WD 160G HD
Sata Seagate 320G HD
XFX GeForce 7600GT XXX edition
Soundblaster Audigy 4
PCI Twinhan Satellite tuner card
Viewsonic VX924 LCD screen
Logitech G15 Keyboard
Logitech G7 Mouse
Ipod
Epson R300 Printer

I've tried the following distros so far...
Ubuntu 6.10 Desktop
Ubuntu 6.10 Ultimate
Ubuntu 7.04 Desktop

I've tried with everything pulled out of my computer except the DVD drive, 1 Sata drive, video card, sound card, lcd monitor and Twinhan card.

I've tried disabling ACPI settings in bios, running IHC8R and JMicron controllers as IDE, RAID, and AHCI in all possible combinations.

I've tried different sata drives, I've tried connecting to different sata ports.

I've tried the following command line options in the Ubuntu installer in various combinations..  acpi=off, pnpmode=off, noapic, nolapic, irqpoll, all-generic-ide

I've seen about 3 or 4 different problems depending on my configuration.  Sometimes I get a PNPBios error and it says something about not running MMCONFIG, then I get the tty error and a prompt.

Somtimes it says the Jmicron controller is in dual mode, then proceeds to give me I/O errors on hda all at the same location.  This has happened with different sata drives connected.

One time it actually seemed to discover 3 HDD's, it got to hdc and then just hung.

Never have I gotten to the Ubuntu desktop.  I only get the install screen and after I select install, I get the status bar.  I always press <alt>-F2 to see the log and it always fails with one of the above problems.

Rob W.

---

### Post by Kateikyoushi on 2007-03-06
I would recommend to try the alternate cd, that's your best bet.

---

### Post by Brockoli on 2007-03-06
I downloaded the alt. cd last night.  I'll try it tonight.  I've been wondering though, what is different about the alternate cd?

Rob W.

---

### Post by Kateikyoushi on 2007-03-06
It uses text mode to install after a minimal system is set up you can configure the rest to your liking.

May I ask did you make the other identical thread ?

---

### Post by Brockoli on 2007-03-06
> **Kateikyoushi said:**
> 

May I ask did you make the other identical thread ?

I did.  I didn't notice until you pointed it out.  When I made the post, my browser hung.  I clicked the post button a second time but I thought it didn't go through either time actually.  I left it alone and when I came back, the post went through...twice. :(  I marked the other one as resolved, I guess I can't actually delete it.

Rob W.

---

### Post by poohbear1616 on 2007-03-06
> Sometimes I get a PNPBios error
Having plug-n-play enabled in the bios can sometimes cause snags.

I posted this in your resolved thread also.

I have to pay better attention...:lolflag:

---

### Post by Brockoli on 2007-03-07
I got it installed last night!  Thanks for the help guys.  I'm going to post my bios settings in case it is helpful for anyone else.  See top of thread for my hardware.  Here are the bios settings on my p5b deluxe wi/fi/  These aren't all the settings, just the ones that I was playing with trying to get linux installed.  Any other settings would have been the factory defaults.

ICH8R  IDE mode
Jmicron IDE mode
ACPI settings both on
USB legacy support auto
Onboard audio turned off (using SB audigy)
Onboard firewire off (don't use it)
Both NIC's on (only one of them works so far in Ubuntu)


Distro used to install: Edgy Alternative text mode

Everything was detected and is working except one of the nic's on the motherboard.

Rob W.

---

