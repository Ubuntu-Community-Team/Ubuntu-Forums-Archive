---
title: "black screen after &quot;enable frame buffer&quot;"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by Karcsi on 2005-07-26
Hi,

I am absolutely new to linux with no experience. I read in a newspaper about Ubuntu and thought it worse trying. The columnist was really fascinated about it and praised the easiness and user friendliness of the system and they installed it on an old machine. I downloaded the Live CD (Ubuntu 5.04 Hoary Hedgehogand) to try it on the old laptop that I have.

Laptop:
IPC Topnote 340S2 (it is the same as Gericom Weblog 340S2 according to web sources)
Intel Centrion processor
666 MHz
64 MB Ram
SIS 5513 Dual PCI IDEcontrol
SIS 630 Graphic card
SIS 900 PCI Ethernet adapter
Although, these things do not tell me too much since I have little knowledge of hardware. Currently Windows ME is installed on it.

To get to the point, the Live CD installation stops after the message 
"Trying to enable frame buffer". Just a black screen and I have to unplug the laptop.
I made some searches and found on the forums that people experience similar problems with laptops and Live CD but the installation CD works. I tried that one too, but exactly the same problem. I also tried the server mode without success.

Could someone please give some advise?

---

### Post by mingus on 2005-07-26
[QUOTE=Karcsi] . . . the Live CD installation stops after the message 
"Trying to enable frame buffer". Just a black screen and I have to unplug the laptop.
[/QUOTE]

At the boot prompt trying typing:  live vga=771

---

### Post by Karcsi on 2005-07-29
It worked. Many  thanks. 
Also on the installation CD if I typed "install VGA=771".

However, I would be interested what caused  the problem or what does this "vga.." do?

Regards

---

### Post by mingus on 2005-07-30
[QUOTE=Karcsi]It worked. Many  thanks. 
Also on the installation CD if I typed "install VGA=771".

However, I would be interested what caused  the problem or what does this "vga.." do?

Regards[/QUOTE]

The VGA command instructs the framebuffer driver to use a particular video resolution/color depth, expressed in decimal as follows:

     640x480  800x600 1024x768 1280x1024
256 	769 	771 	773 	 775
32K 	784 	787 	790 	 793
64K 	785 	788 	791 	 794
16M 	786 	789 	792 	 795

Framebuffer is a software abstraction layer that enables text to be displayed in "graphical" mode even though the graphics system (Xserver) has not been started yet.  When the boot messages are scrolling, it is framebuffer that makes the text display nicely in many columns rather than like the raw text you see for example from the BIOS when you first turn on the system.

When the Xserver runs, it can take a video configuration hand-off from the framebuffer or (typically) will usually use a driver specific to the video card,   In other words, there is usually one video driver used during boot (and for text tty text sessions) and another for the Xserver.  The universal framebuffer driver is vesafb.

Vesafb if usually given a video resolution parameter in the kernel boot argument (in the grub menu), that is the "vga=xxx".  Sometimes vesafb has trouble communicating with the video card, often that can be remedied by dropping the resolution parameter.  Now that you know 800x600 will work, try the value 773 if you want 1024x768.  Again, bear in mind this is not the same as your Xserver configuration used for gnome.

---

