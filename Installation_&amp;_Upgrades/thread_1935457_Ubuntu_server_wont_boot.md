---
title: "Ubuntu server wont boot"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Baunsbol on 2012-03-04
Hi.

I have installed ubuntu server 10.04 on my new setup.. But after the installation and reboot nothing happends

I just have a empty black screen with a white line that blinks just after the manufactor logo

I dont know what im doing wrong or where im doing it wrong.

The hardware is:

Mobo: Intel S1200KP server board
CPU: Intel Xeon E3-1225 
Ram: Kingston value ram 1x2GB

Hope you can help me.


Edit:

Im using a 2GB usb pen for installing if that have anything to do with it.

---

### Post by winh8r on 2012-03-04
Okay, first thing is this, there is no Graphical User Interface on Ubuntu 10.04 Server, so you will not have a Desktop Environment. 

Administration of the server is done via the command line.

May I ask you your reason for installing a server?

---

### Post by darkod on 2012-03-04
When you were installing did you notice any error about installing the bootloader? Did you select to install the bootloader to the MBR of the disk?

---

### Post by Baunsbol on 2012-03-04
@winh8r -  know there is nothing else than a comand line... but the only thing i can do at that screen is to reboot the system (ctrl+alt+del)... other that that i cant do nothing and it doesnt do anything when i type something.

the point of it is a nas server(media server with streaming transcoding, ftp and torrent server) with a ventrillo server.


@darkod - it doesnt promt me with any errors other than if i want to write the grub boot loader to the system hdd... whatever option i choose doesnt make any difference.



btw the only experience i got with ubuntu is a little desktop... so i dont know that much about it

---

### Post by darkod on 2012-03-04
If you can, boot it with the standard desktop live cd into live mode, and run the boot info script from the link in my signature. Post the results as explained there. It should show more details.

---

### Post by Baunsbol on 2012-03-04
i will try that as soon as i get home and put a dvd drive into it.

---

### Post by winh8r on 2012-03-04
My apologies, I read your first post and it looked to me like you had installed Ubuntu server and were expecting it to boot into GUI mode or something, that was why I was asking why you needed a server.


Slight misunderstanding , that's all.

---

### Post by MAFoElffen on 2012-03-04
> **Baunsbol said:**
> Hi.

[COLOR=Red]I have installed ubuntu server 10.04[/COLOR] on my new setup.. But after the installation and reboot nothing happends

I just have a empty black screen with a white line that blinks just after the manufactor logo

I dont know what im doing wrong or where im doing it wrong.

The hardware is:

Mobo: Intel S1200KP server board
CPU: Intel Xeon E3-1225 
Ram: Kingston value ram 1x2GB

Hope you can help me.


Edit:

Im using a 2GB usb pen for installing if that have anything to do with it.
Logical triage:

1. If you hold down the shift key right after the BIOS messages does your Grub Menu display? 
 a) If it does display, you have 2 seconds to press an arrow key to keep it displayed.
 b) If does not display, try to press the shift key repeatedly while booting.
 c) If does not display, then boot up on LiveCD and changed the grub default file to hardcode display the menu. If you need to do this I'll give you instructions.
 d.) If it still doesn't display, reinstall Grub, because it apparently doesn't seem to to working.

2. The Grub Menu Displays... Verified that Grub is installed. Edit the boot line to include a Linux VESA mode such as
a) ```

vga=791

```b) If that doesn't work, try 788, 785, 772 or 770
c.) If none of those worked to boot the kernel, reinstall the system.

---

### Post by Baunsbol on 2012-03-11
Hi again


After i had to put in a dvd drive i tried to install from a disc and that went without any errors.. So problem fixed :)

Boots like a charm now.

---

