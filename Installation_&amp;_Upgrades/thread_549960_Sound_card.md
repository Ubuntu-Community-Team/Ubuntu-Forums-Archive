---
title: "Sound card"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Larjk on 2007-09-13
Hello, I can't make working the sound on my Ubuntu Feisty. Also I don't know the model of my sound card, and if I try to execute the command "alsamixer", it doesn't work, telling to me an error.
What command must I use to know the model of my sound card, and what must I do to make it working?
Thanks in advance and Greetings

---

### Post by dreadlord_chris on 2007-09-13
open a terminal:
```

lspci

```
and post the contents....

---

### Post by Larjk on 2007-09-14
Ok, the contents are this:

> 
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 3372
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
02:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)


---

### Post by dreadlord_chris on 2007-09-19
sorry for not getting back to you sooner - this has been a really bad week for me...

looks like you have the VIA AC97 HDA controller - so I do believe these would be your drivers:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154)

---

