---
title: "Need help installing ubuntu, Stuck at black screen!"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by lobfredd on 2010-04-01
I am trying to install ubuntu on my dekstop computer, i put in the cd it boots, i choose language, and when i get the menu where i can start ubuntu from cd, install it etc. Whatever option i press enter at, i am stuck at a black screen with a flashing white _ in left top corner
I am using an external usb dvd drive.
i tried the same usb dvd drive at my laptop and the white _ was there for just some seconds and then ubuntu started doing what it should.

Speqs:
CPU: Intel Core 2 Quad Q6600	
Motherboard: Abit IP35 PRO	
Memory: Mushkin XP2 RedLine PC8000 1000Mhz	
Graphics Card: 4870x2
Hard Drive: Intel x25

please help and sorry for my English

---

### Post by quadproc on 2010-04-01
> **lobfredd said:**
> I am trying to install ubuntu on my dekstop computer, i put in the cd it boots, i choose language, and when i get the menu where i can start ubuntu from cd, install it etc. Whatever option i press enter at, i am stuck at a black screen with a flashing white _ in left top corner
I am using an external usb dvd drive.
i tried the same usb dvd drive at my laptop and the white _ was there for just some seconds and then ubuntu started doing what it should.

Do you get an option of starting in safe video mode?  If so, does that bring up a usable login screen?

I think that I know what the problem is, but to be sure I need to ask which version of Ubuntu are you using?

Let's assume that you are using a version with the problem that I know about.  First, I will describe the problem.  The X server identifies your graphics device(s) during its startup and if it finds more than one (you indicate that you have two 4870s, so do I) then it needs to know which one is the primary device (in other words, which one to use to interact with the user).  If there is no identification of the primary device then the X server just gives up and does not start.  The result is that you get a command line interface and no graphics.

If this is happening then one experiment that you could try is power down the system, remove the secondary graphics card, and then power up and reboot.  If it succeeds then you have this problem.

To get around this problem, you can add a BusID specification to your xorg.conf file on the primary device.  To find out what BusID to use, do a ```
lspci | grep ATI
```You will see something similar to > 02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
03:00.1 Audio device: ATI Technologies Inc HD48x0 audioFigure out which is the primary card (the one that your monitor is plugged into) and use its BusID in your /etc/X11/xorg.conf file by modifying the Device section to add that BusID.  That part of my xorg.cong file looks like
> Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSectionOf course, you should use the numbers that you saw in your lspci output.

Because the xorg.conf file is a system file, you will need to be root to modify it so you could use gksudo gedit /etc/X11/xorg.conf to do the editing.  Substitute a different editor if you prefer something else.

The new xorg.conf file will be read the next time that you boot the system, and if everything is right then you should get a graphics screen.

Good luck!

quadproc

---

### Post by megahost on 2010-04-01
Try going into your BIOS and making the first boot-up option is from your CD/DVD drive. I'm sure once you have that selected will also look for such peripherals like the thumb drive

---

