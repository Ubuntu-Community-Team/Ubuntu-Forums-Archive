---
title: "Installation of ubuntu using a USB Drive"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Chileshe_Nduna on 2014-12-08
I do not have a DVD Rom Drive and would like to install Ubuntu 14 on my laptop. I have changed the boot order in bios to boot from my USB but nothing happens.
Is it possible to install Ubuntu from my USB Drive? Please help!

---

### Post by grahammechanical on 2014-12-08
On my machine the BIOS sees a USB memory stick as a USB external drive. And just as in your case changing th boot order is not enough. To boot from the USB memory stick I have to go into a setting for hard drives and select which drive to boot from. If there is such a setting in your BIOS you may see a USB external drive listed underneath the hard drive.

Regards.

---

### Post by fel3 on 2014-12-08
> **Chileshe_Nduna said:**
> I do not have a DVD Rom Drive and would like to install Ubuntu 14 on my laptop. I have changed the boot order in bios to boot from my USB but nothing happens.
Is it possible to install Ubuntu from my USB Drive? 


[http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html](http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html)

> [COLOR=#333333][FONT=arial]When your PC is first starting [/FONT][/COLOR][up]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-UPS")[COLOR=#333333][FONT=arial] — also known as booting up — it looks for the operating system. Should you need to troubleshoot, it is helpful to know where it looks and in what order. Depending on the problem, you may need to change the order.[/FONT][/COLOR][COLOR=#333333][FONT=arial]The *boot order* is the sequence of storage devices that the computer’s [hardware]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-hardware") checks to find an operating system. As luck would have it, an operating system can lurk in several places:[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**[Hard]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-hard_drive") [drive]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-hard_drive"):** This is the main storage device for most PCs. More than one hard drive may be in your computer, and those hard drives may be *partitioned* into separate, *logical* drives. The *master boot record* (MBR) on the primary hard drive holds a map that indicates where the operating system can be found or provides a boot menu to select an operating system.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**SSD:** Eventually, the solid state drive will replace the hard drive as the PC’s primary storage device. Internally, the SSD is composed of [flash]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-flash_memory") [memory]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-memory"), just like a thumb drive or[media]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-media_card") [card]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-media_card"), but with a much higher capacity (and price). Externally, an SSD works just like a hard drive with an MBR and partitions.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**Optical drive ([CD]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-CD")-[ROM]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-ROM")/[DVD]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-DVD")):** Even when you don’t choose the optical drive as the primary boot device, many PCs automatically detect a bootable disc in the optical (CD or[DVD]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-DVD_drive")) [drive]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-DVD_drive"). When that happens, an option is [displayed]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-display") on the [screen]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-screen"), something like [FONT=courier]Press Enter to boot from the CD or DVD[/FONT]. Press the Enter key to direct the computer to start from that disc on the fly.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**[Network]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-network") ([Ethernet]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-Ethernet")):** Rather than load an operating system from the PC’s own (local) storage devices, the network option directs the computer to load its operating system from the network. On start-up, the [network]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-networking_adapter") [adapter]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-networking_adapter") requests an operating system to load, which it then downloads from the server.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]**[USB]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-USB") device:** The USB device can be a thumb drive, a media card, or an external [disk]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-disk_drive") [drive]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-disk_drive"). This option is useful for [laptops]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-laptop") that lack optical drives, allowing you to install or [upgrade]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-upgrade")your PC’s operating system.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]You set the boot order in the PC’s Setup [program]("http://www.dummies.com/how-to/content/change-the-boot-order-on-your-pc.html#glossary-program"). Generally, the steps go like this:[/FONT][/COLOR]

[LIST]
[*]Restart or turn on the computer.

[*]Press the key or keys to enter the Setup program.
As a reminder, the most common key used to enter the Setup program is F1.
Ensure that you press the key to enter the Setup program or menu. Do not press the key to enter the boot menu, which is a different item.

[*]Choose the menu option or options to display the boot sequence.
The option may not be obvious from the Setup program’s main menu, not to mention that the Setup program is in Text mode. Various computers I’ve researched display the menu that changes the boot order in these ways:

[LIST]
[*]Startup&#8594;Boot

[*]Boot&#8594;Boot Device Priority

[*]Advanced BIOS Features&#8594;(various priority submenus)

[*]System&#8594;Boot Sequence
[IMG]http://media.wiley.com/Lux/58/290258.image0.jpg[/IMG]
[/LIST]

[*]Set the boot order.
Use whichever keys or techniques are required in order to set the sequence in which the hardware searches the storage devices for an operating system.

[*]Save the changes and exit the Setup program.
The computer restarts with the new settings.
[/LIST]
[COLOR=#333333][FONT=arial]You might see other options in addition to those that set the boot sequence search order. For example, you might see a way to exclude certain devices from being searched. This might be a good idea for USB media cards or for legacy floppy drives.[/FONT][/COLOR]

:razz:

---

### Post by Darth Riker on 2014-12-08
> **Chileshe_Nduna said:**
> I do not have a DVD Rom Drive and would like to install Ubuntu 14 on my laptop. I have changed the boot order in bios to boot from my USB but nothing happens.
Is it possible to install Ubuntu from my USB Drive? Please help!

Just a question - when you built the Live USB drive did you use the method outlined here (I'm assuming you have access to a Windows machine): [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by oldfred on 2014-12-08
You have to correctly create a bootable device.
Most of the install software assumes smaller flash drives and erases the entire thing. It extracts ISO and installs a boot loader so BIOS or UEFI can see that flash drive is a bootable device. (you cannot just copy ISO to drive except with a dd command which also erases entire drive).

How did you install Ubuntu installer to your external drive? For BIOS to boot it, it must have a boot loader on it.

---

### Post by ubfan1 on 2014-12-08
Furthermore, some new UEFI machines (e.g. Asus X200CA) seem to require that secure boot be turned off before USB will boot, even when it is first in the boot order.

---

