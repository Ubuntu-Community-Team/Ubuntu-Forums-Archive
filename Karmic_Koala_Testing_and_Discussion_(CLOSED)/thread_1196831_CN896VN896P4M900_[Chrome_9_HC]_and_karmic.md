---
title: "CN896/VN896/P4M900 [Chrome 9 HC] and karmic"
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-06-25
i'm using the original via hp mini 2133... i know i know, i should have waited for an intel graphics card and it was so cute..
anyway

how am i to get
the graphics working?

i've tried so many things
but no luck..

what exactly is the issue?
is it a module mismatch, i read that somewhere...
is it the new version of Xorg? what do i do?


someone please help.

my lspci says the following:

```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
```


please helpp

---

### Post by sintacto on 2009-06-25
you may need the openchrome driver works pretty good for me
Driver "openchrome"
to /etc/X11/xorg.conf

---

### Post by puccaso on 2009-06-26
how exactly do you get your openchrome working?!

i get a nothing screen

can you send a copy of ur xorg.conf? cheers.. also, i'm assuming u have the original 2133 with the via chipset right?

---

### Post by sintacto on 2009-06-29
sorry for the wait
I dont have a laptop but the via pc3500g motherboard

VIA pc3500 Mainboard Specifications
# Form Factor 	Micro-ATX, 190.5mm x 228.6mm
# Processor 	1.5/1.8 GHz VIA C7®-D processor
# Bus speeds up to 400/800MHz, NanoBGA2 package
# Chipset 	North Bridge: VIA CN896
# South Bridge: VIA 8237A or VT8237S (supports SATA II)
# System Memory 	2 DDR2 DIMM slots (400/533/667 MHz)
# Up to 2GB memory size
# VGA 	Integrated VIA Chrome9™ DirectX® 9.0 HC Graphics core with Chromotion™ CE
# MPEG-2 decoding accelerator
# Supports 64/128/256 MB Frame Buffer size


i got this going

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "openchrome"            
EndSection

Section "Module"
        Load  "glx"  
        Load  "dri"
EndSection

Section "DRI"
        Mode         0666
EndSection

below works for me too


Section "Device"
	Identifier	"Configured Video Device"
        Driver          "openchrome" 
EndSection         


good luck

---

