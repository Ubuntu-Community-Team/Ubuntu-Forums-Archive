---
title: "linux newbie : stuck during install"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by Jahoe on 2004-12-21
hello,

I am a linux newbie. Only experience is a one time install of Mandrake and one time SuSe. Now I am trying Ubuntu. I hava a pc here with a XP installation. I boot it with the ubuntu cd ans just started the install. It detects hardware etc. But then it stops/hangs in a blue screen with white bar at the bottom. No disk activity at all. Anyone a clue? Can it be some hardware incompatibality?  (PIII 850, 256 sdram, 8GB disk)

---

### Post by deshantm on 2004-12-21
Can you explain what the screen looks like more?

At what point of the installation are you?

---

### Post by Jahoe on 2004-12-21
screen is clear blue as it is during the installation. At the bottom there is a white bar , full width of the screen. It is in the first stage of setup. I can choose language, keyboard etc. then it starts detecting discs etc. Then the progression bar closes and all is left is the blue screen with white bar without any text

---

### Post by wallijonn on 2004-12-22
What type of video card do you have?

Have you disconnected any and all USB devices (other than mouse. Maybe.)

---

### Post by Jahoe on 2004-12-23
no usb devices. dont know exactly the video card type. I will check.  I just got the system from a friend. It has a gigabyte Slot1 P3 mainboard with a p3 - 850. with only one ps/2 connector for mouse. Keyboard has still the older DIN type connector.  Is there a list of supported hardware for Urbuntu/linux/debian? Or is that a stupid question

---

### Post by Jahoe on 2004-12-27
[QUOTE=Jahoe]no usb devices. dont know exactly the video card type. I will check.  I just got the system from a friend. It has a gigabyte Slot1 P3 mainboard with a p3 - 850. with only one ps/2 connector for mouse. Keyboard has still the older DIN type connector.  Is there a list of supported hardware for Urbuntu/linux/debian? Or is that a stupid question[/QUOTE]
 For nknow reasons the installation seemed to go ok now. I let the system do the partioning (one ext3 partition and a swap) After the first reboot it halts with this text on the screen:

GRUB loading stage 1.5.

Grub Loading, please wait...
Error 18

---

### Post by Nathanael Reveal on 2004-12-28
I'm not sure if this will be useful, but I've been working to understand the Grub Error 18 problem. Try this: use the BIOS Hard Disk auto detection and choose the "Normal" option, not the LBA mode option. Reboot the machine and see if GRUB will boot properly.

---

### Post by pupsa on 2004-12-28
[QUOTE=Jahoe]hello,

I am a linux newbie. Only experience is a one time install of Mandrake and one time SuSe. Now I am trying Ubuntu. I hava a pc here with a XP installation. I boot it with the ubuntu cd ans just started the install. It detects hardware etc. But then it stops/hangs in a blue screen with white bar at the bottom. No disk activity at all. Anyone a clue? Can it be some hardware incompatibality?  (PIII 850, 256 sdram, 8GB disk)[/QUOTE]
 Hi!

I had the same situation.

In expert mode, select "no DHCP" in the network configuration.

Mine then carried on.

Hope it helps

---

### Post by Jahoe on 2005-01-06
setting the disk to normal iso LBA in BIOS solved the installation problem.  I can now start ubuntu and login with the given username. But when i want to start the gui with "startx" I get errors : 

(EE) Problem parsing config file
(EE) Error from xf86handleconfigfile()

Fatal Server Error: no screens found 

XIO : Fatal IO error 104 (connection reset by peer) on X server ":0.0"after 0 requests (0 known processed) with 0 events remaining

jan@ubuntu:~$ 

I think something went wrong during installation of packages, I'll try to reinstall the whole thing

---

### Post by NewbieNik on 2005-01-06
I am also getting the Error 18 message from GRUB on a new install onto an old HP Netserver LH Pro (ATI Mach 64 PCI card). This is using a SCSI HP NetRAID disk system and a AIC-7800 controller for CD, both of which Ubuntu Warty is detecting and formatting fine.
Install runs perfectly as it has on another 2 systems (Basic IDE Pentium 4s), but on initial reboot system hangs. (Powers off as if to reboot, but doesn't - restarting using reset button or manual power-off brings error)

I have tried using:-

custom pci=noacpi

Install, but same error occurs. I have had Mandrake 9.2 running at one point, but had to disable the battery monitor and command-run services before it would boot.

Anyone any ideas???

Please don't make me go back to FC3

---

