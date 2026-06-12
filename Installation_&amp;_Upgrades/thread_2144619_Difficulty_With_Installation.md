---
title: "Difficulty With Installation"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by Fangorn513 on 2013-05-12
Hello,

I am having some difficulty with installing Ubuntu. I would appreciate any advice.

What is happening:

I am trying to install Ubuntu 13.04 on to a Toshiba NB255-250. I downloaded Ubuntu 13.04 from ubuntu.com and used a program from pendrivelinux.com to make a bootable USB drive (the computer doesn't have a disc drive). Following the completion of the USB drive, I put it in to the Toshiba and started the computer and went to the setup and changed the default boot to the USB drive and then shutdown. Starting up the computer I get the normal Toshiba screen followed by the screen flashing something that I can't read (it is really quick). Then the window says:

```
graphics initialization failed
Error setting up gfxboot
boot:
```

This screen dose nothing if left alone. However I found that if you enter help and then press enter or as I found later F1, then I get a new screen.

```
Welcome to Ubuntu!

This is an installation system for Ubuntu 13.04
It was built on 20130424

HELP INDEX

KEY     TOPIC
<F1>   This page, the help index.
<F2>   Prerequisites for installing Ubuntu.
<F3>   Boot methods for special ways of using the system.
<F4>   Additional boot methods; rescue mode.
<F5>   Special boot parameters, overview.
<F6>   Special boot parameters for special machines.
<F7>   Special boot parameters for selected disk controllers.
<F8>   Special boot parameters for the install system.
<F9>   How to get help.
<F10>  Copyrights and warranties.


Press F2 through F10 for details, or ENTER to boot:
```

If I press enter it will boot from the drive and display Ubuntu and have all the features  This is where I am having the most difficulty I would like to do a full install so I don't have to have the USB drive always in the computer.

I have read through the whole help index (I won't type all of the pages because that would take a long time) however the just of it is that it should install if I type in install in to the command prompt. I have tried this and it returns an error. The help says that some computers need all preferences to be be stated in the command. I am not sure what to enter in, here is the page (F6) that refers to the difficulty:

```
SPECIAL BOOT PARAMETERS - VARIOUS HARDWARE


you can use the following boot parameters at the boot: prompt.
in combination with the boot method (see <F3>)
If you use the hex numbers you have to use the 0x prefix (e.g., 0x300).

HARDWARE                    PARAMETER TO SPECIFY
IBM PS/1 or ValuePoint (IDE disk)        hd=cylinders,heads,sectors
Some IBM ThinkPads                       floppy.floppy=thinkpad
Protect I/O port regions                 reserve=iobase,extend[,...]
Laptops with screen display problems     vga=771
Use first serial port at 9600 baud       console=ttyS0,9600n8
Force use of generic IDE driver          all_generic_ide=1
Possible (temporary) workarounds for locckups or other hardware failures:
disable buggy ACPI interrupt routing     noapic nolapic
(partly) disable ACPI                    acpi=noirq or acpi=off
disable USB                              nousb
poll for interrups                       irqpoll

For example:
   boot: install vga=771 noapic nolapic

Press F1 for the help index, or ENTER to boot:
```

If you anyone can tell me what to type in or how to get the full install menu (this one is the command prompt version) that would be really great.

---

### Post by hansdown on 2013-05-12
Welcome to the forum,
Fangorn513.

Press enter to boot.

When ubuntu is up and running, you should see an 

> Install ubuntu

icon on the desktop.

Double click that, and choose to install.

Do you wish to dual boot; click install side by side.

Completely install ubuntu(will erase other operating systems).

Choose "other", if you are comfotable with partitiong.

---

### Post by Fangorn513 on 2013-05-14
Thanks Hansdown,

The advice was really helpful. I've got my system up and running; it works great.
I feel kinda bad that I didn't see the icon on the desktop. I probable never would have noticed it if you hadn't pointed it out. Thanks a bunch.

---

